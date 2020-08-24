#StudioAlerts2
Using Twilio Studio for Voice and SMS Alerts

Use Case: Call a number to invoke an incident alert to a list of people via phone call. If person one does not answer, try again with person 2. Continue iterating over the list. (Initially built to support 3 users (including initial caller) for demo.)

The Flow:

1. Caller calls a phone number connected to Studio flow: Alerts-Inbound.
2. Press 1 to create new incident call or enter PIN to join existing call.
3. After pressing 1 to start new incident call, create a PIN.
4. After creating PIN, caller is sent a text message confirming, and then added to a conference with that PIN.
5. Studio flow: Alerts-Outbound is launched from within the inbound flow, passing:
    - Participant 1 name and phone number
    - Participant 2 name and phone number
    - PIN
6. Outbound call is dialed to Participant 1.
7. If no answer or if answering machine, send text message with incident bridge details and iterate to particpant 2, repeating steps 5 and 6 for participant 2.
8. If a human answers, connect to the bridge with the initial caller.

Files:
  Alerts-Inbound.json: Inbound call flow representing steps 1 through 5 above.
  Alerts-Outbound.json: Outbound call flow, initiated through REST API from Alerts-Inbound, represented by steps 5 through 8 above.
