---
title: "Network connection"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by OldDog11 on 2007-03-23
I'm trying to connect to a network.

In network settings I started to configure a wireless connection but now it seems to have just disappeared. When I go into network setting the only option is a modem connection. 

Any ideas where my wireless connection went?

---

### Post by martinw89 on 2007-03-23
Type "iwconfig" into a console.  It should show a wireless card.  If it doesn't you either have a driver problem or your wireless card got disconnected somehow.

-Martin

---

### Post by OldDog11 on 2007-03-23
It says:

lo  no wireless extensions

sit0 no wireless extensions

---

### Post by martinw89 on 2007-03-23
Can you tell us what wireless card you have?  If it is external (USB) make sure it's in securely, the same goes if it's a PCMIA card (a card that goes into the side of your laptop).  From iwconfig's output it looks like you have no wireless cards installed.  If it was working before it's most likely a loose card or a driver issue.  Have you tried rebooting?  A process controlling your card may have quit, rebooting would start it again.  These are all just shots in the dark, I hope something helps.

---

### Post by OldDog11 on 2007-03-23
I have a USB adapter, how do I reconnect it?

---

### Post by martinw89 on 2007-03-23
Try unplugging it from the computer and plugging it into another USB port.  Also make sure all connections are clean and that it doesn't have any hair or anything like that stopping a connection.  If the USB cable is separate from the adapter, make sure both ends of the cable are clean.

---

### Post by proudpedestrian on 2007-04-02
if you type in the command "lsusb" it will show what is pluged into the usb ports and if you see your wireless card's name there it is in right.

---

