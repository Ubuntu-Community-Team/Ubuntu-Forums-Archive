---
title: "PCI Card"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Jayzon11 on 2008-02-10
My motherboard has no options be it a jumper or bios to turn off the intergrated video, is there a console command to blacklist the darn thing.

---

### Post by Cypher on 2008-02-10
Some Mobo's will default to using a video card in a particular slot if it is available, short of that since the hardware is always going to be on, the software is going to find it and try to use it.

But if you have an extra video card as well, that should also be found and perhaps you can  configure it for use and ignore the integrated one..

---

### Post by spiderbatdad on 2008-02-10
if you know the driver from xorg.conf you can blacklist it in /etc/modprobe.d/aliases

---

### Post by Jayzon11 on 2008-02-10
I'll try that and post my results when in a little bit

---

