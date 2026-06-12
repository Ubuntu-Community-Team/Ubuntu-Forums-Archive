---
title: "Default Essid at Boot"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by avalonpimp on 2007-04-04
Hi i am running a server install, with fluxbox as my WM. On boot my wireless card connects automatically to the wrong access point (linksys) and i need it to connect to mine on startup (221b).
So each time i log in, i have to issue these commands. 
 sudo iwconfig wlan0 essid 221b
 sudo dhclient wlan0
 - then i get a new ip and connected to correct ap

So using wirelesstools commands from console or where do i tell ubuntu to connect to 221b at startup, or where would i put a script to excute these commands at boot>??

Any ideas?

---

### Post by drakazz on 2007-04-04
> **avalonpimp said:**
> Hi i am running a server install, with fluxbox as my WM. On boot my wireless card connects automatically to the wrong access point (linksys) and i need it to connect to mine on startup (221b).
So each time i log in, i have to issue these commands. 
 sudo iwconfig wlan0 essid 221b
 sudo dhclient wlan0
 - then i get a new ip and connected to correct ap

So using wirelesstools commands from console or where do i tell ubuntu to connect to 221b at startup, or where would i put a script to excute these commands at boot>??

Any ideas?

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
I hope it helps

---

### Post by avalonpimp on 2007-04-04
Solution for the uBUNTU COMMUNITY


Adding it to /etc/network/interfaces

/etc/network/interfaces is the file where your network interfaces are defined, eth0 being the standard wired interface. To make the wireless network come up when you start your computer put # in front of 'auto eth0' (to stop it automatically starting) and add something like the following lines.

auto wlan0
iface wlan0 inet dhcp
wireless-essid   MYNETWOTK
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed



- or in my case just added 'wireless-essid 221b'
and the rest i filled in

---

