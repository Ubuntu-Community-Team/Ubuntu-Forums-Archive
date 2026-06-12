---
title: "wireless feisty"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by natman on 2007-04-28
I just installed feisty on my desktop with a usb wireless adapter( ratlink chip set i think, made by cable and wireless).
Feisty detectd the wireless device and even the SSID but when i give it the wep key, it just stalls and a few min later error in connection could not connect.

Am i totally screwed or can i get it to work?

---

### Post by Game_boy on 2007-04-28
I got it to half-work by changing the router to channel 6, but basically most people have unbelievable problems with wireless in feisty - looks like the general consensus is to stay with Edgy Eft.

---

### Post by annda on 2007-04-28
you can see it it really works in the terminal:

iwconfig

will thell you what your wireless interface is called eth1, wlan0, ath0 or something like that.

then do:

iwconfig eth1 scan

substituting eth1 for your interface and see if it picks up APs.

if it does, then you will have to check the WEP key carefully. also, in my experience, ubuntu has problems with handling keys if they are not the first. check your router's settings to see if the active key is at the top of the list.

---

### Post by vanadium on 2007-04-28
I have it working after disabling the "roaming". Then it jsut works as in Edgy.

In System - Administration - Network, right click "Wireless connection" and uncheck "Roaming mode" (the automatic detection of networks. Then make sure you enter your wireless network name and password if you have a secured network. I find my wireless network to be much more stable than under Windows XP.

---

