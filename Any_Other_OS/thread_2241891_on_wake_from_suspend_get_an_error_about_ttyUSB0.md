---
title: "on wake from suspend get an error about ttyUSB0"
date: 2014-08-29
forum: Any Other OS
---

### Post by dave131 on 2014-08-29
I don't have hibernate as an option on my laptop, but it is set to suspend when I close the lid.  It works fine that way - but there is an error message something to the effect of could not initialize ttyUSB0 or some such thing (if you need the exact message I'll have to suspend and wake up a few times so I can get it written down.

At any rate, I didn't know if this is something that makes one of my USB ports unusable.  So far I think they have all seemed to work ok.   I found the following with dmesg, and it looks like it is referring to my wireless, but my wireless still works also on the wake up from suspend.

```
[ 4269.728196] usb 7-2: USB disconnect, device number 4
[ 4269.728499] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 4269.728526] option 7-2:1.0: device disconnected
[ 4269.729043] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 4269.729066] option 7-2:1.1: device disconnected
[ 4269.976087] usb 7-2: new full-speed USB device number 5 using uhci_hcd
[ 4270.132244] usb 7-2: New USB device found, idVendor=413c, idProduct=8133
[ 4270.132253] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 4270.132258] usb 7-2: Product: Novatel Wireless CDMA
[ 4270.132262] usb 7-2: Manufacturer: Novatel Wireless Inc.
[ 4270.137363] option 7-2:1.0: GSM modem (1-port) converter detected
[ 4270.137625] usb 7-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 4270.139229] option 7-2:1.1: GSM modem (1-port) converter detected
[ 4270.139409] usb 7-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 4270.589381] wlan0: authenticate with 00:26:f3:dd:93:b8
[ 4270.600774] wlan0: send auth to 00:26:f3:dd:93:b8 (try 1/3)
[ 4270.602558] wlan0: authenticated
[ 4270.604120] wlan0: associate with 00:26:f3:dd:93:b8 (try 1/3)
[ 4270.612946] wlan0: RX AssocResp from 00:26:f3:dd:93:b8 (capab=0xc11 status=0 aid=3)
[ 4270.613729] wlan0: associated
```

---

### Post by dave131 on 2014-08-29
I guess the log confuses me more.  I know the wireless I use in the computer is bcm4312, but the log is also showing something about GSM modem and Novatel Wireless CDMA.  There isn't a modem port on the laptop.  I know I opened up the case once to check the memory (had to reseat one of them) and it shows some kind of other card in there plus the wireless.  I *think* it is used to connect to the internet via a cellular network, if that's even possible.  Can anyone tell me what these two other entries are for?

I also took the time to keep suspending and waking the laptop until I could get the full error message written down:

Option ttyUSB0: option_instat_callback: error -2.

The only USB device I have plugged in is a USB receiver for a wireless mouse.  I tried moving it to another USB port on the other side of the laptop, but the message still references ttyUSB0.  Could this be that GSM modem or NovatelWireless CDMA things that I have no clue what they even are?

---

