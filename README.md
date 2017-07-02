<!--
title: AWS Send SMS Message with Twilio example in NodeJS
description: This example demonstrates how to send SMS messages with the Twilio SDK and AWS lambda.
layout: Doc
-->
[![Made with Serverless](https://img.shields.io/badge/serverless-⚡-yellow.svg?style=flat-square)](https://serverless.io) [![Norfolk JS Inspired](https://img.shields.io/badge/NorfolkJS-inspired-f3df49.svg?style=flat-square)](https://norfolkjs.org)

# Send SMS Message with Twilio

<img align="right" width="316" height="103" src="https://s3-us-west-2.amazonaws.com/assets.site.serverless.com/blog/twilio-logo.jpg">
This example demonstrates how to send SMS messages with the Twilio SDK and AWS lambda.

[Live the live demo](http://twilio-serverless-example.surge.sh)

## Use Cases:

* Sending users confirmation text messages

## Setup - 

1. [Set up your AWS Credentials](https://serverless.com/framework/docs/providers/aws/guide/credentials/)

2. Sign up for a [Twilio account](http://www.twilio.com)

3. Create a [new phone number](https://www.twilio.com/console/phone-numbers/) in your Twilio trial account

4. Grab your ACCOUNT SID and AUTH TOKEN from the [Twilio console](https://www.twilio.com/console) and plug those into the `env.json` file in the next step

5. Create `env.json` variables in `serverless.yml` with your Twilio account values

  ```yml
  environment:
    # replace these env variables with your twilio account values
    TWILIO_ACCOUNT_SID: ${file(./env.json):TWILIO_ACCOUNT_SID}
    TWILIO_AUTH_TOKEN: ${file(./env.json):TWILIO_AUTH_TOKEN}
    TWILIO_PHONE_NUMBER: ${file(./env.json):TWILIO_PHONE_NUMBER}
  ```

5. Invoke the function and send an SMS message

  Update the `to` phone number the `event.json` file and `message` to send in the SMS

  Then invoke the function with the serverless CLI. Set the `--path event.json` so the function knows where to send the SMS.

  ```bash
  serverless invoke -f sendText --path event.json
  ```

6. (Optional) Deploy the front-end application

  Update the `API_ENDPOINT` variable in the `/frontend/index.html` file and deploy the `/frontend` folder to a static host of your choice.