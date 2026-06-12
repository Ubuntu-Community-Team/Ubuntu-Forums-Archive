---
title: "Wireless"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by netham45 on 2007-03-17
Ok, So far I have gotten NDISwrapper to scan my network... on startup.

It does one scan then I can't scan anymore, it just pauses for a second then says no results.

I have tried with the default drivers that come w/ ubuntu(they scanned, but never connected, didn't let me set WEP either) then I put ndiswrapper on.

I would greatly appricate some help.

Running Ubuntu 6.10 Edgy

WIFI card -- Belkin F5D7010 Wireless G card Ralink V1

Using Driver CD for XP w/ ndiswrapper

Edit: I got it to refresh w/ an iwlist scan on more than the first try(upgraded to the latest ndiswrapper, from 1.8****), but still no connection.


Edit: Got it
I am currently using ndiswrapper 1.38 w/ wifi-radar.

wicd only connected correctly to 'naked' routers.

---

### Post by terdon on 2007-03-17
How are you trying to connect? 
You can try wlanassistant for a graphical tool. Also, check out 
[ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---

### Post by netham45 on 2007-03-17
I've tried 3 methods, wicd, wifi-radar, and using iwconfig / dhclient wlan0

---

