---
title: "Installed Ubuntu, need more help"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by edman2 on 2006-08-21
Ok so I installed ubuntu on my second drive using the alternate cd, and everything worked fine. Now I need to setup my wireless card. I have a linksys wireless g card with speedbooster. I think the model is wmp54gs. Can anybody help?

---

### Post by edman2 on 2006-08-21
bump

---

### Post by DSn0wMan on 2006-08-21
I dont use this card myself, but my guess is that you will have to do something with ndiswrapper(use winddows drivers for linux). I found this article/how-to.

[http://dossy.org/archives/000110.html](http://dossy.org/archives/000110.html)

I hope this helps.

---

### Post by gils0040 on 2006-08-21
if you type iwconfig does anything show up like ra0? have you checked system->administration->networking?

---

### Post by gils0040 on 2006-08-21
after looking a little more into it, you will not have you to ndiswrapper. it looks like your cards uses the broadcom chipset. check this site outhttp://bcm43xx.berlios.de/?go=Home

---

### Post by edman2 on 2006-08-22
okay so I posted this in the wireless forum but I thought I'd do so here too since this is my original post..

Ok so I just installed ubuntu, and for the most part I'm a complete newbie at linux. I've read a few things about installing the wireless card (linksys wireless g w/ speedboost wmp54gs), but they have been very confusing. Some say to use NdisWrapper some say to not etc...I don't even know where to start.

When I type in iwconfig I get the following:

lo no wireless extensions.

eth0 IEEE 802.11b/g ESSID: off/any Nickname:"Broadcom 4306"
Mode:Managed Access Point: Invalid Bit Rate=1 Mb/s
RTS thr: off Fragment thr: off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.


When I type in "lspci -v" i get this:

0000:00:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
Subsystem: Linksys: Unknown device 0015
Flags: bus master, fast devsel, latency 32, IRQ 12
Memory at ed000000 (32-bit, non-prefetchable) [size=8K]

Can someone point me in the direction I need to go (keeping in mind I know very little about linux).

---

### Post by edman2 on 2006-08-22
bump

---

### Post by edman2 on 2006-08-22
can someone please help me out here?

I followed the link from gils up above, and in the documentation i ended up on this site [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

Do I follow the instructions on there? I'm a little confused...I guess according to it I don't have to use ndiswrapper, but I get a little confused on how to do the rest.

---

### Post by edman2 on 2006-08-22
bump

Ok well I guess nobody can help me with this. I've searched the forums but I still don't really know what direction to go and I'm afraid that I might just screw something up. I guess I'll try the site up above and hope it works....

---

