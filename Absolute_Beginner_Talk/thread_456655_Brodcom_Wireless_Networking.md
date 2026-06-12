---
title: "Brodcom Wireless Networking"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by astrosoup on 2007-05-27
I am working on a Compaq laptop with a dreaded Broadcom 4306 card. I had the card working to the point where WiFi Radar would recognize it, then updated to Feisty Fawn and fiddled with it to get it recognized again (installed ndiswrapper, etc.). But as far as I can tell, Wi-Fi radar should have some sort of "connect" button or something, and it doesn't. It finds my network as well as several neighboring ones, but it never connects to anything. Creating an additional connection does not help me either. The "Edit" "Delete" and "Disconnect" buttons warrant no response. Network manager doesn't connect for me either, under static or dynamic IP. For the sake of experiment I am trying mostly on a unsecured 802.11g network (managed). I am brand new to Linux, so I'm not sure where to go from here. Feisty Fawn can detect my card and enable it (the little blue wlan light comes on), but I can't get it to connect. This wasn't working under my previous version of Linux either. :( Can anyone help me?

---

### Post by GWoitena on 2007-05-28
Try using fwcutter from synaptic and get rid of wifi radar.  fwcutter did it for me.  Then go into network manager and make sure your wireless card is NOT selected and roaming is checked.

---

