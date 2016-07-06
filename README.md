# This plugin is under the development

[![CircleCI](https://circleci.com/gh/treasure-data/embulk-input-google_analytics/tree/master.svg?style=svg)](https://circleci.com/gh/treasure-data/embulk-input-google_analytics/tree/master)

# Google Analytics input plugin for Embulk

Embulk input plugin for Google Analytics reports.

## Configuration

- **json_key_content**: See example config.
- **view_id**: View ID for target data. You can find it on [Google Analytics page (you need a permission to access Admin page](https://lucidpress.zendesk.com/hc/en-us/articles/207335356-Find-your-Google-Analytics-Tracking-ID-View-ID) (string, required)
- **time_series**: Only `ga:dateHour` or `ga:date` (string, required)
- **dimensions**: Target dimensions (array, default: `[]` )
- **metrics**: Target metrics (array, default: `[]` )
- **start_date**: Target report start date (string, default: [7 days ago](https://developers.google.com/analytics/devguides/reporting/core/v4/rest/v4/reports/batchGet#reportrequest))
- **end_date**: Target report end date (string, default: [1 day ago](https://developers.google.com/analytics/devguides/reporting/core/v4/rest/v4/reports/batchGet#reportrequest))

## Example

```yaml
in:
  type: google_analytics
  json_key_content: |
    {
      "type": "service_account",
      "project_id": "....",
      "private_key_id": "....",
      "private_key": "-----BEGIN PRIVATE KEY-----\n..........................\n-----END PRIVATE KEY-----\n",
      "client_email": ".....",
      "client_id": ".........",
      "auth_uri": "https://accounts.google.com/o/oauth2/auth",
      "token_uri": "https://accounts.google.com/o/oauth2/token",
      "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
      "client_x509_cert_url": ".........."
    }
  view_id: 123111111
  time_series: "ga:dateHour" # hourly basis
 
  # https://developers.google.com/analytics/devguides/reporting/core/dimsmets
  dimensions:
    - "ga:browser"
  metrics:
    - "ga:visits"
    - "ga:pageviews"

  start_date: "2016-06-27"
  end_date: "2016-06-28"
```


## Build

```
$ rake
```
