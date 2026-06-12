---
title: "Unable to connect to some Wi-Fi networks"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by jerrylin on 2007-11-29
I have been using Ubuntu for a long while now, and I am always able to connect to my personal wireless network in my apt. When I am on campus, the wireless network is open (no authentication), I can see the signal (and good strength) but I cannot connect. I have been trying with the default network manager.

Everyone I have asked has been able to connect fine, so I assume its something I'd have to change on my end. Anyone have any suggestions?

Hardware:
Dell Inspiron 9400 laptop
WiFi card - Intel 3945ABG
Ubuntu 7.10 Gutsy

---

### Post by gigaferz on 2007-11-30
type in terminal 

iwlist scan
sudo iwconfig wlan0 essid nameofnetwork  
sudo dhclient wlan0


this has always worked for me,

if you need more options type" man iwconfig",
 for example look at my  command
sudo iwconfig wlan0 essid homenet mode Managed rate 54M key open s:jugger

---

