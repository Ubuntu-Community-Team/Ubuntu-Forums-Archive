---
title: "Wireless Internet is not being found."
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Islington on 2006-07-02
I upgraded to dapper and my wireless internet card : network everyhere NWK11B
isnt even being detected. This card and subsequently the internet service 'just worked' on the previous version of ubuntu (5.10). I dont know what to do, I am a complete noob. I couldn't even find a wiki page to help. The weird thing is that when I updated and rebooted, internet worked. Then this morning I booted up, hoping to show off, and kaboom, no internet. I open up the *system>>Admin>>network* and the card doesnt even show (it used to show as wlan0),and the modem isnt configured.This absolutely is a downer, I am back to using winxp.Any help? suggestions? links?Is there a way to manually add the card (*add hardware in windows*)?


I am awaiting my dapper cd. maybe a fresh install will help?

---

### Post by Islington on 2006-07-02
Noone is having/has had this problem?

---

### Post by Apple 101 on 2006-07-03
Use *ndiswrapper* to keep the card on your system permanently.  You also need *wireless-tools*, *wpa_supplicant* and *ndisgtk* (in Universe) (optional, but configures ndiswrapper for you!)

---

### Post by Islington on 2006-07-03
[QUOTE=Apple 101]Use *ndiswrapper* to keep the card on your system permanently.  You also need *wireless-tools*, *wpa_supplicant* and *ndisgtk* (in Universe) (optional, but configures ndiswrapper for you!)[/QUOTE]
Thanks for the reply. Will I still be able to install these without internet? Also synaptic is having errors with the sources list, is there anywhere I can get a clean one?

---

