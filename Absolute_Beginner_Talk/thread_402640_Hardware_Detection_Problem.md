---
title: "Hardware Detection Problem"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by JonniePee on 2007-04-06
Hey guys.

I jsut got my new Compal Hel80 system today from powernotebooks.com. its a sager model 2080. Specs: > 1 Sager NP2080 FORCE - $1,450.00
   15.4" WSXGA+ (1680 x 1050) "Matte" LCD w/PCI-e nVIDIA GeForce Go 7600 w/256MB
   Intel® Core™2 Duo T7200 2.0GHz Processor  w/4M L2 On-die cache - 667MHz FSB
   2,048MB (2 SODIMMS) DDR2/667 Dual Channel Memory
   100GB SATA/150 Hard Drive at 7,200 RPM
   Combo Dual Layer DVD +/-R/RW CD-R/RW Drive w/Softwares
   4-in-1 Memory Card Reader (MS/MSPRO/SD/MMC)
   Built-in Intel® PRO/Wireless 3945 802.11a/b/g
   9-cell Smart Li-ion Battery
   Full Range Auto Switching AC Adapter
   NO Floppy Disk Drive
   NO Operating System

I installed Ubuntu 6.10 onto it, everything went fine. For some reason, however, when I go to device manager, pretty much all of the devices are unknown. Any ideas?

I think this problem might be linked to my second obstacle. When I go to install the OGL drivers for the Nvdia Go 7600. I get X-Server errors upon reboot and I can't get back into the desktop. It says somethign along the lines of Nvidia Device not found. 

I am new to linux in general, so I apologize for not knowing the ropes. Any help would be most graciously appreciated. Thanks in advance. :KS

---

### Post by crispy_420 on 2007-04-06
So you think the main issue is with NVidia drivers? Just for starts try to edit your xorg to only list vesa as driver. That will get you a gui again to mess around with. So:

nano /etc/X11/xorg.conf

Change the section under Section "Device" driver to "vesa".

---

### Post by JonniePee on 2007-04-06
I just finished reinstalling Ubuntu again. This is the 3rd time, i tried again before and did the same driver install and it failed again. so what approach should i take on round 3? haha

---

### Post by JonniePee on 2007-04-06
got it :-) thanks for the help

---

### Post by crispy_420 on 2007-04-06
So my suggestion worked?

---

### Post by powderhound99 on 2007-04-12
I just got pretty much the same machien except the hd is 80g I loaded fiesty fawn and at first nothing but my wireless card worked through filling dependencies and updates my Nvidia card works. I'm now running Beryl i suggest you do the same when possible. As for other devices such as bluetooth and my card reader I'm still having issues but it seems to be getting better with every update if anyone has suggestions I'd be elated. Until then keep digging and good luck.:guitar:

---

### Post by powderhound99 on 2007-04-12
btw what about your integrated camera? I've seen a post for a bug in fiesty about the thinkpad camera not working any issues with 6

---

