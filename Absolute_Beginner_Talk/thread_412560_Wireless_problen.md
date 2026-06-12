---
title: "Wireless problen"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Henningselst on 2007-04-18
Hi, i just installed Ubuntu (dualboot). But this ain't windows and Ubuntu does not automatically connect to the net:P Iv got a D-link DWL-G510 (H/W Ver.: C2) and i need some step by step help to get it working. If you could provide me with that i would be very happy :D I've tried to read the forums for help but i cant figure out anything from that. I'm a bit to green.

---

### Post by mikeyphi on 2007-04-18
is your wireless connector listed under SYSTEM - ADMINISTRATION - NETWORKING?
If yes - highlight and set properties.
If no - you need to find a driver. Go here for further help:  [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

---

### Post by Henningselst on 2007-04-18
Ok, i looked under SYSTEM - ADMINISTRATION - NETWORKING
And i found two Wireless connections. One called (wmaster0) And the other called (Wlan0)
So i guess this means that Ubuntu found my card. If that is so how do i search for wireless networks in the area?

---

### Post by Fenrirwulf on 2007-04-18
You can run in console

iwlist wlan0 scan

Once you know hte SSID you can then go into Network Manager and add that to your cards configuration.

---

### Post by Fenrirwulf on 2007-04-18
You can also open Synaptic Package Manager and do a search for 'Wireless'. I found some good utilities that find wifi AP's for you like in win-doh's. :D

---

