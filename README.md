# Ogo
An OpenFlow Network Controller in Go

## Subscribing to OpenFlow Messages
Use `ogo.SubscribeTo(ofp10.OFPM_*)` to get an ofp10.OfpMsg chan.
```
echoRequestChan := ogo.SubscribeTo(ofp10.OFPT_ECHO_REQUEST)
```

## Acting on Messages
The function `Listen()` is required for all Applications. Use this function to listen for messages on your subscription channels.
```
(app *OgoApplication) Listen() {
for {
    select {
      case msg := <- app.echoRequestChan:
        fmt.Println("Recieved an EchoRequest message from:", msg.DPID)
    }
  }
}
```
