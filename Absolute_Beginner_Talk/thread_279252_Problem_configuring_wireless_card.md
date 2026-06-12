---
title: "Problem configuring wireless card"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by suhaib23 on 2006-10-17
I have dell inspiron 1505 with bcm 1390 wireless card. Its not supported by ubuntu so I used ndiswrapper to install it. For some reasons, the system does not show up this device with iwconfig, however ndiswrapper list both device and driver 
 
sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

with iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

iwconfig wlan0
wlan0     No such device

network setting aplication does not show it either

---

### Post by keithweddell on 2006-10-17
It might not be called wlan0.  Try looking in /etc/modprobe.d/ndiswrapper to see what alias it has.


Keith

---

