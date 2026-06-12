---
title: "Cannot get wireless to work on my iBook G4"
date: 2008-05-29
forum: Apple Hardware Users
---

### Post by ethand320 on 2008-05-29
Hi guys,

I just recently installed ubuntu on my iBook g4 labtop which has a wireless card that i had been using on the mac operating system.  However ubuntu does not seem to pick up my wireless card and i cannot connect to the internet.

any advice would be greatly appreciated.

---

### Post by tamoneya on 2008-05-29
please copy and paste the result of ```
lspci
``` onto the forums so we can get a better look at your hardware

---

### Post by ethand320 on 2008-05-29
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)

---

### Post by Kerri on 2008-05-30
Hi
Fwcutter is installed and you've got a problem when it try to extract the firmware, that is?

If yes, install this package:
[http://kambing.ui.edu/debian/pool/contrib/b/b43-fwcutter/b43-fwcutter_011-4_powerpc.deb](http://kambing.ui.edu/debian/pool/contrib/b/b43-fwcutter/b43-fwcutter_011-4_powerpc.deb)

it work for me.

---

