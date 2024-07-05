# Google Assistant: Voice-Controlled Lighting System

This project demonstrates how to create a voice-controlled lighting system using Google Assistant, IFTTT, and the Bolt IoT platform. Follow the steps below to set up and control an LED using voice commands.

## Table of Contents
1. [Overview](#overview)
2. [Hardware Components](#hardware-components)
3. [Software and Online Services](#software-and-online-services)
4. [Steps](#steps)
   1. [Hardware Setup](#step-1-hardware-setup)
   2. [Getting the Bolt API Key and Device ID](#step-2-getting-the-bolt-api-key-and-device-id)
   3. [Creating the GPIO Control Command](#step-3-creating-the-gpio-control-command)
   4. [IFTTT Integration via Google Assistant and Webhooks](#step-4-ifttt-integration-via-google-assistant-and-webhooks)
5. [Conclusion](#conclusion)
6. [Credits](#credits)

## Overview

This project allows you to control an LED connected to a Bolt IoT WiFi module using voice commands through Google Assistant. By integrating Google Assistant with IFTTT and the Bolt IoT platform, you can turn the LED on and off with simple voice commands.

## Hardware Components

- **Bolt IoT Bolt WiFi Module** × 1
- **LED (generic)** × 1

## Software and Online Services

- **Bolt Cloud**: [Bolt IoT Bolt Cloud](https://cloud.boltiot.com)
- **IFTTT WebHooks**: [IFTTT Webhooks](https://ifttt.com/maker_webhooks)
- **IFTTT Google Assistant**: [IFTTT Google Assistant](https://ifttt.com/google_assistant)

## Steps

### Step 1: Hardware Setup

1. Connect the longer end of the LED to Pin 0 of the Bolt WiFi module.
2. Connect the shorter end of the LED to the ground pin (GND) on the Bolt WiFi module.
3. Power on the Bolt WiFi module.

### Step 2: Getting the Bolt API Key and Device ID

1. Login to [cloud.boltiot.com](https://cloud.boltiot.com) and note the ID of your Bolt WiFi Module.
2. Navigate to the API Tab and click on "Enable" under the "Generate Key" section.
3. Click the copy button to copy your API key. Your API key will look something like this: `f1f918e9-d9c2-4e5b-aed0-b7cb743f74cf`.

### Step 3: Creating the GPIO Control Command

1. Since the LED is a digital output device, create a Digital Write command to control it via the Bolt platform.
2. Refer to the [Bolt Cloud GPIO Commands API Documentation](https://docs.boltiot.com/docs/gpio-commands-api#write-digital-output) to create the API command link.
3. The structure of the command is:
   ```
   https://cloud.boltiot.com/remote/API_KEY/digitalWrite?pin=PIN_NUMBER&state=HIGH/LOW&deviceName=DEVICE_ID
   ```
4. Replace the parameters with your own values:
   - `API_KEY`: Your API key from the API tab on the cloud dashboard.
   - `PIN_NUMBER`: The pin number where the LED is connected (0, 1, 2, 3, or 4).
   - `HIGH/LOW`: Indicates the LED state (`HIGH` to turn on, `LOW` to turn off).
   - `DEVICE_ID`: The ID of your device from the cloud dashboard.
5. Example command to turn on the LED connected to device ID `BOLT13819450` on pin 0:
   ```
   https://cloud.boltiot.com/remote/g1g818f7-y9c1-5e7c-aed1-t7bi941h54of/digitalWrite?pin=0&state=HIGH&deviceName=BOLT12345678
   ```

### Step 4: IFTTT Integration via Google Assistant and Webhooks

1. Go to [IFTTT](https://ifttt.com) and create a new applet.
2. Log in using your Gmail account (the same account used on your mobile device for Google Assistant).
3. Click on "+This" to create the trigger.
4. Choose Google Assistant -> Say a specific phrase.
5. Enter the phrase to trigger the action (e.g., "Turn the lights on").
6. Click "Create Trigger".
7. Click on "+That" to create the action.
8. Select Webhooks -> Make a web request.
9. Enter the API URL created in Step 3.
10. Set Method to `GET` and Content-Type to `application/json`.
11. Click "Create Action" and then "Finish".

#### Steps to Turn OFF the LED

1. Repeat the above process to create a command to turn off the LED.
2. Change the `state` parameter to `LOW` in the API command:
   ```
   https://cloud.boltiot.com/remote/g1g818f7-y9c1-5e7c-aed1-t7bi941h54of/digitalWrite?pin=0&state=LOW&deviceName=BOLT12345678
   ```

## Conclusion

Congratulations! You have successfully created a voice-controlled lighting system using Google Assistant, IFTTT, and the Bolt IoT platform. Now you can control your LED with simple voice commands through Google Assistant.
Developers are requested to use this section per their project implementations' requirements, and contributions are always welcomed.
Thank you.
