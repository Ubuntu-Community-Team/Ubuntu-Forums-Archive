---
title: "I need WUSB54G v4 help"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Lkr on 2007-07-15
My installation of Ubuntu 7.04 went well on my Dell XPS 400.  Now my only problem is wireless.  It detects the card, and when I put in my network key for my network, it simply will not connect.  Anyone have any help?:popcorn:

---

### Post by linuxwizard on 2007-07-15
Look over this might have some info that will help you

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4?highlight=%28WifiDocs%2FDevice%29)

---

### Post by uputer on 2007-09-23
I'm wondering which Linksys adapter and version is most compatible or configurable in Linux/Ubuntu. ;)

---

### Post by linuxwizard on 2007-09-23
uputer
Look through links and try to compare. These are the only ones I found.

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29)

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11)

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC)

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GP](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GP)

---

### Post by uputer on 2007-09-23
The WUSB54G ver. 4 adapter has rt2570 chipset so you must use the rt2570 driver?  (note:  WUSB54G wireless *card* has rt2500 chipset, *I think*)

Go to:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

Use CVS rt2570-CVS tarball for this adapter and/or chipset.  

For the OP, you'd want the rt2500-CVS tarball file since you're using a PCI wireless card.   I'm asking about the usb adapter but if you still have trouble, consider that.

Or:
[http://linux-wless.passys.nl/query_part.php?brandname=Linksys](http://linux-wless.passys.nl/query_part.php?brandname=Linksys)
and:
[http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)

It appears, that for the rt2570 chipset, the rt2571 driver is used.  

Source:  [http://lists.alioth.debian.org/pipermail/pkg-ralink-commits/2007-June/000009.html](http://lists.alioth.debian.org/pipermail/pkg-ralink-commits/2007-June/000009.html)

So, at the Ralink support page, use RT25USB-SRC-V2.08.0.tar.gz ????

This is only if the adapter doesn't work 'out-of-the-box' or if there are issues when using it out of the box.

Does that make sense?

---

