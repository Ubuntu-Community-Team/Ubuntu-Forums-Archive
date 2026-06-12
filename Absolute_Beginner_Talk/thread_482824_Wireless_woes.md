---
title: "Wireless woes"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ColinT on 2007-06-24
Hi All

Running Feisty Fawn 7.04. Just loaded on lads PC which has a wireless connection to my adsl router. Can't get the wireless utility to find any networks let alone my own. Have checked security type / password access etc but still no joy. Is there any way to see if the drivers are there? Card is a Belkin Wireless G which works fine on the XP partition. Any help / pointers appreciated.

Regards

Colin

---

### Post by ugm6hr on 2007-06-24
The following gives useful info to start (paste in Terminal):
```
lspci
lsusb
ifconfig
iwconfig
```
Looking for Ethernet/Network Controller info from lspci to discover chipset of the Belkin card ( lsusb is for usb cards).
With the info from these, it should be possible to help.

---

### Post by bigspottycat on 2007-06-24
I had a similar problem with my Belkin wireless card under Edgy; here's a reply I posted a while back which might help:

[http://ubuntuforums.org/showthread.php?t=274001](http://ubuntuforums.org/showthread.php?t=274001)

Good luck.

---

### Post by mattg89 on 2007-06-24
I have just finally sorted out my Belkin wireless connection. What card is it? USB/PCMCIA? Post up the results of the commands above. Most of the drivers are already in the kernel for the Belkin one's now, it's probably just a matter of configuring it.

---

### Post by shifty_powers on 2007-06-24
Or there is always the possibility of ndiswrapper to utilise the windows drivers. certainly made my life a hell of a lot easier....

---

