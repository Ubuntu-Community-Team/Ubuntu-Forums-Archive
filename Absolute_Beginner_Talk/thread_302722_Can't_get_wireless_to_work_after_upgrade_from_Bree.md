---
title: "Can't get wireless to work after upgrade from Breezy to Dapper"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by andym1966 on 2006-11-19
Hi,
I've just installed Dapper Drake over my Breezy Badger installation.  Wireless used to work fine before but now, when I go to System>Administration>Networking and select properties on my Wireless Connection, my whole system freezes.  The only thing I can do is turn off my machine. 

The Ethernet connection is active by default - could this have anything to do with it? I've deactivated it and gone back into the wireless connection properties but it still freezes.

I have an Averatec 3200 laptop with built in wireless, and I'm a linux newbie!

Any help/suggestions greatly appreciated.

Andy.

---

### Post by andym1966 on 2006-11-20
Hi All,
I got a reply to this help request on [www.averatecforums.com](www.averatecforums.com).

************
It (the update) likely overwrote your xorg.conf, which needs some help to keep the wireless and the video from reacting badly.

Here's the relevant section from my xorg.conf for my 3270:
Code:

Section "Device" 
Identifier "Via Unichrome" 
Driver "via" BusID "PCI:1:0:0" 
Option "DisableIRQ" 
Option "EnableAGPDMA" 
EndSection


DisableIRQ in particular should stop that freeze from occurring. The file that needs to be edited can be found in /etc/X11, and again is named xorg.conf.
************

I checked my xorg.conf file and it was missing the two Option lines.  I added them in and restarted my machine, and the problem was solved.  Wireless connection properties no longer freezes!  Good stuff!

---

