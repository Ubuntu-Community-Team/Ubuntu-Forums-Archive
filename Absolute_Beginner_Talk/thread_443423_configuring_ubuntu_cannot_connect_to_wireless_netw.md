---
title: "configuring ubuntu: cannot connect to wireless network"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Tanja on 2007-05-14
Hi there,

This is my first ever post :) 

I am trying to connect to the internet through the office wireless network.

I have tried to activate it by network settings, and also with the commands

sudo iwconfig eth1 key XXXXXXXX

sudo iwconfig up

But it's not working. What should I try?

THANK YOU VERY MUCH.

---

### Post by blazercist on 2007-05-14
What kind of wireless card do you have? 

Type sudo iwconfig and give us the output.

---

### Post by Tanja on 2007-05-14
Thanks!

This is the output:

lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by blazercist on 2007-05-14
Ok its looks like you have no ESSID set try setting the ESSID

sudo iwconfig eth1 ssid <your ESSID here>

also, you haven't told me what kind of Wifi card you're using.

Have you tried this with the network-manager app?

System> Administration>Networking> enter your password and select your essid from the drop down menu.

---

