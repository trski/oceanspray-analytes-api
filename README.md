# Ocean Spray Analytes API

## Headers

```
Content-Type: application/json
```

## Authentication

```
$URL?token=api_token
```

## Routes

### Get Analyte

`GET /v1/samples/:sampleId/analytes/:eurofinsCode`

Response
```javascript
[
  {
    "id": 1802464,
    "sampleId": 14052,
    "chemClassCode": "OT",
    "analyteId": 46,
    "eurofinsCode": "7300A305",
    "testStatus": 5500,
    "detectionResult": 0.6,
    "analystName": "jdoe",
    "detectionResultDate": "2021-03-06T00:00:00.000Z",
    "auditUpdatedBy": "System",
    "auditCreatedBy": "System",
    "auditCreateDate": "2021-06-10T09:44:47.367Z",
    "deleted": 0,
    "auditUpdateDate": "2021-06-10T09:44:47.367Z"
  }
]
```

### Get Analytes

`GET /v1/samples/:sampleId/analytes`

Response
```javascript
[
  {
    "id": 1802453,
    "sampleId": 14052,
    "chemClassCode": "OT",
    "analyteId": 2,
    "eurofinsCode": "7300A148",
    "testStatus": 5500,
    "detectionResult": 0.8,
    "analystName": "jdoe",
    "detectionResultDate": "2021-03-06T00:00:00.000Z",
    "auditUpdatedBy": "System",
    "auditCreatedBy": "System",
    "auditCreateDate": "2021-06-10T08:56:40.100Z",
    "deleted": 0,
    "auditUpdateDate": "2021-06-10T08:56:40.100Z"
  },
  {
    "id": 1802454,
    "sampleId": 14052,
    "chemClassCode": "OT",
    "analyteId": 3,
    "eurofinsCode": "7300A157",
    "testStatus": 5500,
    "detectionResult": 0.4,
    "analystName": "jdoe",
    "detectionResultDate": "2021-03-06T00:00:00.000Z",
    "auditUpdatedBy": "System",
    "auditCreatedBy": "System",
    "auditCreateDate": "2021-06-10T08:56:40.100Z",
    "deleted": 0,
    "auditUpdateDate": "2021-06-10T08:56:40.100Z"
  }
]
```

### Create Analyte

`POST /v1/samples/:sampleId/analytes`

Request
```javascript
{
  "eurofinsCode": "7300A135",
  "detectionResult": 0.4,
  "analystName": "jdoe",
  "detectionResultDate": "2021-03-06T00:00:00.000Z"
}
```

Response
```javascript
{"status": "success"}
```

### Create Analytes

`POST /v1/samples/:sampleId/analytes-bulk`

Request
```javascript
{
  "data": [{
    "eurofinsCode": "7300A148",
    "detectionResult": 0.8,
    "analystName": "jdoe",
    "detectionResultDate": "2021-03-06T00:00:00.000Z"
  },
  {
    "eurofinsCode": "7300A157",
    "detectionResult": 0.4,
    "analystName": "jdoe",
    "detectionResultDate": "2021-03-06T00:00:00.000Z"
  }],
  "validate": true
}
```
NOTE: the `validate` attribute can be set to the
boolean `true` so that Ocean Spray will run sample
validation. If `validate` is missing, `null`, or any
value other than the boolean `true`, then Ocean Spray
will not run validation on the sample, allowing
the developer to continue to make modifications
to the sample as needed.

Response
```javascript
{
  "status": "success",
  "inserts": 2,
  "failures": 0,
  "validate": true
}
```

### Validate Sample

`POST /v1/samples/:sampleId/validate`

Response
```javascript
{
  "processed": true
}
```

### Update Analyte

`PUT /v1/samples/:sampleId/analytes/:eurofinsCode`

Request
```javascript
{
  "detectionResult": 40,
  "analystName": "jdoe",
  "detectionResultDate": "2021-06-06T00:00:00.000Z"    
}
```

Reponse
```javascript
{
  "status": "success",
  "message": [{
    "ProtectiveScreenSampleId": 14052,
    "AnalyteId": 71
  }]
}
```

### Get Sample

`GET /v1/samples/:sampleId`

Response
```javascript
[
  {
    "Id": 14052,
    "SampleNumber": "0001",
    "ResampleNumber": "0",
    "CropYear": 2021,
    "BedHistoryId": 507392,
    "SampleTrackingStatus": 2309,
    "Sampler": null,
    "ExpectedHarvestDate": "2021-03-11T00:00:00.000Z",
    "Export": true,
    "CmRequested": false,
    "EbdcRequested": false,
    "OcRequested": false,
    "OpRequested": false,
    "FerbamRequested": false,
    "OtRequested": false,
    "PhiConfirmed": false,
    "SampleTypeId": 1,
    "OverrideFlag": false,
    "ReceivedBy": "jdoe",
    "DateReceived": "2021-03-05T00:00:00.000Z",
    "Comments": null,
    "OtaRequested": false,
    "OtsRequested": false,
    "OtiRequested": false,
    "OtcRequested": false,
    "Lab": "Lakeville",
    "ResampleSuffix": "0",
    "SampleDate": "2021-03-05T11:52:50.230Z",
    "LabId": 2,
    "DateSampleCollected": "2021-02-15T05:00:00.000Z",
    "CollectedBy": "Company",
    "SentVia": "UPS",
    "DateSampleSent": "2021-03-17T04:00:00.000Z",
    "SentBy": "Lanco",
    "LabBinNumber": 1,
    "DateSampleTested": "2021-06-09T16:18:30.323Z",
    "TestedBy": "jdoe",
    "Audit_UpdatedBy": "foo",
    "Audit_CreatedBy": "bar",
    "Audit_CreateDate": "2021-02-12T15:49:27.937Z",
    "Audit_UpdateDate": "2021-06-09T22:53:52.317Z",
    "TimeStamp": null,
    "Deleted": false,
    "HasOverrideDeliveryClearance": false,
    "OverrideDeliveryClearanceComments": null,
    "ExportResultTolerance": false,
    "OverrideResampleComments": null,
    "StatusDateChanged": "2021-06-09T13:23:57.030Z",
    "StandardScreen": false,
    "ThirdPartySampleId": null,
    "ThirdPartySentDate": null
  }
]
```
