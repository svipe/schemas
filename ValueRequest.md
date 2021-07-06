
### Value Requests

Sometimes you want to request only claims with specific values. If the End User is not in possession of such claims they can not respond. Examples include only Swedish people or those in possession of a vaccination certificate or maybe an employee pass or only a certain subject.

Vaccination:

```
{
  "claims": {
    ..
    "certificate": {
      "value": {
        "schema": "some schema URL",
        "type": "some schema type definition"
      }
    }
    ..
  }
}
```

#### Example: Request Corona Vaccination Certificate

To request a EU Green Card certificate the schema is https://id.uvci.eu/DGC.combined-schema.json and the valid types are vaccination|test|recovery.


```
{
  "claims": {
    ..
    "certificate": {
      "value": {
        "schema": "https://id.uvci.eu/DGC.combined-schema.json",
        "type": "vaccination"
      }
    }
    ..
  }
}
```

And the response will be:

```
{
  "claims": {
    ..
    "green_certificate": {
      "value": {
        "schema": "https://id.uvci.eu/DGC.combined-schema.json",
        "type": "vaccination",
        "vaccination_entry": {
          "tg": string, // "Disease or agent targeted"
          "vp": string, // "Vaccine or prophylaxis"
          "mp": string, // "Vaccine medicinal product"
          "ma": string, // "Marketing Authorization Holder - if no MAH present, then manufacturer"
          "dn": string, // "Dose Number"
          "sd": string, // "Total Series of Doses"
          "dt": string, // "Date of Vaccination"
          "co": string, // "Country of Vaccination"
          "is": string, // "Certificate Issuer"
          "ci": string, // "Unique Certificate Identifier: UVCI"
       } 
       "payload_string": string // the full original contents of the QR code
      }
    }
    ..
  }
}
```

in a general case:

```
{
  "claims": {
    ..
    "certificate": {
      "value": {
        "schema": "some url",
        "type": "some type",
       "payload_string": string // the full original contents of the QR code
      }
    }
    ..
  }
}
```

Employee:

```
{
  "claims": {
    ..
    "certificate": {
      {"essential":true}, 
      "value": {
        "type": "ericsson_employee_number"
      }
    }
    ..
  }
}
```


A certain subject:

```
{
  "claims": {
    ..
    "sub": {"value": "248289761001"}
    ..
  }
}
```
