---
title: "Xorg requires root for 1600x1200 but 1280x1024 is ok"
date: 2006-06-24
forum: Bug Reports / Support
---

### Post by ShamoIdol on 2006-06-24
Got strange behavouir of Xorg after migrating from SuSE to Dapper.
Xorg refuses to run at 1600x1200 as a regular user, the maximum it can shows is 1280x1024 (which I belive is max for VESA standart or something like that).
So I tried to run it as root (Xorg :1 vt6) and connect to it using startx (startx -- :1 vt6). In this way everything is fine. But when I run the X server is run as a regular user it doesn't give any errors in its log but simple runs at 1280x1024.

The card is "Intel Corporation 82852/855GM Integrated Graphics Device".
Driver is i810.

When I tried to switch driver to vesa it runs at 1600x1200 with no problem (except vesa driver is much slower).

I think it has something to do with Debian/Ubuntu because the video system ran perfectly with RedHat and SuSE.

---

### Post by bscbrit on 2006-06-24
[http://ubuntuforums.org/showthread.php?t=203047](http://ubuntuforums.org/showthread.php?t=203047)

This thread has just solved a similar problem - might be worth checking to see if yours has the same symptoms and/or cause.

---

