---
title: "Where could I get firmware-b43-installer and b43 for ibook powerpc ?"
date: 2016-12-21
forum: Apple Hardware Users
---

### Post by mrj22 on 2016-12-21
Hi All,
   Currently I cleaned up my ibook g4 PowerPC and installed Ubuntu 10.04 PowerPc version on it, it works normal except no wifi connection.
I searched on the internet for a while invalid. I got a file b43-fwcutter_012_1build1_powerpc.deb, and tried to install it by sudo dpkg -i b43*deb , but it got errors
since no network connection.  I have tried to find a file broadcom-wl*bz2 , there is always not a right one -- they seem not a powerpc version ! How could I get the right
ones for ibook powerpc ? many thanks for solutions !

I type lspci -vnn | grep 14e4  it shows a message below

0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

and dmesg shows huge volume of message (skipped)

---

### Post by oldfred on 2016-12-21
Duplicate Closed.
See:
[https://ubuntuforums.org/showthread.php?t=2347092](https://ubuntuforums.org/showthread.php?t=2347092)

---

