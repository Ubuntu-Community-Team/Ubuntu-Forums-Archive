---
title: "blender on ubuntu and xp"
date: 2008-02-09
forum: Art &amp; Design
---

### Post by mosaic2s on 2008-02-09
Friends,

i first used blender on xp, liked it.

now i have it installed in ubuntu gutsy. however the menu buttons give a garbled screen around text when accessed. strange. can not figure it out.

---

### Post by eye208 on 2008-02-09
It's probably a display driver issue.

---

### Post by RemmyLee on 2008-02-09
Agreed. Can you post your system specs? We can point you to an installation guide for the driver pertaining to you card.

---

### Post by mosaic2s on 2008-02-10
AMD 2800+ 1GB RAM. 80 GB HDD ATA. 17" LCD BENQ. no graphic card.

same problem seen on the system while running

ubuntu 7.04
ubuntu 64bit gutsy
and now 32bit gutsy.

would be glad to know and get it rectified.

---

### Post by eye208 on 2008-02-10
> **mosaic2s said:**
> no graphic card.
To find out the name of your VGA controller, enter the following into a terminal window:
```
lspci | grep VGA
```

---

### Post by mosaic2s on 2008-02-12
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

---

### Post by legatek on 2008-02-12
I find blender doesn't work if I have desktop effects enabled (both Edgy and Feisty with Beryl). Try switching your system to Metacity before running Blender.

---

### Post by mosaic2s on 2008-02-12
Since i do not have a graphic card, beryl does not work on my system. my desktop interface is basic with no visual effects.

---

### Post by RemmyLee on 2008-02-12
Would that be an AMD XP 2800 or a Sempron 2800?

Mesa should be kicking in there and although you won't get breakneck speeds, with a gig of ram it should run smoothly enough to make very usable.

---

### Post by mosaic2s on 2008-02-14
hi there, system is AMD ATHLON XP 2800+.
what is mesa - haven't heard this till now.

---

