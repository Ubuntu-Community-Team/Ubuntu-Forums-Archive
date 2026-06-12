---
title: "No wireless connexion (Airport / PPC)"
date: 2009-02-05
forum: Apple Hardware Users
---

### Post by abelthorne on 2009-02-05
Hello,
I've installed Ubuntu PPC on an iMac G5. So far, all goes quite well, I've managed to setup the system with no major issue.

But there is a problem I can't seem to solve. My iMac G5 is "Airport Extreme-ready", which means it doesn't have wireless connectivity as a default option but contains a slot for an Airport card. I bought one a few monthes ago and it works well with MacOS X.

With Ubuntu, that's another story : it seems the card is detected (lspci finds **0001:01:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**), it is detected by the Hardware devices manager, I've activated it but:
- it doesn't see any wireless network in the NM menu
- it can't connect to one I manually add

I've tried a few how-to's, in case the firmware files were different, to no avail.

Any idea of what I can do to use my wireless access as expected (having an ethernet cable running through the middle of the room is not really practical) ?

EDIT : I've just installed wifi-radar and when running it from the terminal, I get **wlan0     Interface doesn't support scanning : Network is down** errors. How can I fix this ?

---

