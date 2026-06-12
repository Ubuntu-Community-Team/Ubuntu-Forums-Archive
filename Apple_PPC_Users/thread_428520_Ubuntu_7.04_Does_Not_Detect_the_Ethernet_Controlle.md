---
title: "Ubuntu 7.04 Does Not Detect the Ethernet Controller of Mac Mini /G4"
date: 2007-04-30
forum: Apple PPC Users
---

### Post by freiubtheit on 2007-04-30
Hi,

Having successfully installed Ubuntu 7.04 onto my external Firewire Linux Partition, I noticed that the newly install Ubuntu does not detect my ethernet controller at all.

Details of the ethernet controller obtained through "lspci -v" is as follows:

0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev ff) (prog-if ff)
       !!! Unknown header type 7

By the way, the result of lsmod is as follows:

Module
sbp2
ohci1394
ieee1394


Please help get the ethernet port up for my Mac Mini G4.

---

### Post by badgerclan on 2007-04-30
Haven't had any problems with mine.

0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
        Flags: bus master, 66MHz, slow devsel, latency 16, IRQ 41
        Memory at f5200000 (32-bit, non-prefetchable) [size=2M]
        Expansion ROM at f5100000 [disabled] [size=1M]

Try the following link and look at 10.6.1
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)

---

