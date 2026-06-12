---
title: "does this mean i got my wireless card working?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by dacookiemonn on 2007-06-05
got a 1390 broadcom, here is iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

my light is orange, wheras in vista, it is blue, i got a switch on the front of the laptop, dv6325
I followed a guide here and a seem to go wwell, except for a .ko file not being int he right place, but I sudo -s and copied it over there and the command took.
not getting any wireless info though, just thought maybe it is supposed to be blue like in vista

---

### Post by happy-and-lost on 2007-06-05
Do an *iwlist eth1 scan* to see if you can see any networks with it

---

### Post by Zzl1xndd on 2007-06-05
it looks like it recognizes the card. What version are you using? if 7.04 are any networks showing up in your list?

---

