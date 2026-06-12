---
title: "GRUB installation error"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Bardobrave on 2007-05-19
Hi.

I´m trying to install Feisty Fawn in an AMD x64 with 2Gb memory and a 200Gb SATA hard drive partitioned with 180 Gb for a ntfs with windows xp and 10 Gb ext3 partition for the Ubuntu.

All seems to be all right until the end of the installation, when a GRUB error pops and installation stops.

I haven´t selected a partition for swap memory during the installation, but I supose that this won´t be the problem. 

Any ideas will be wellcomed.

Thank you all.

---

### Post by vtel57 on 2007-05-19
It could very well be the problem. Linux MUST have a /swap partition.

---

### Post by krisfrajer on 2007-05-19
Try reinstalling ubuntu and let the installers do the job on the free space partition. Maybe that will work the best for you at this point when you are just starting the installation. That is what I will do. You can reduced the size of the swap partition if you do not want it to be taken lots of space of your hard drive. As a rule of thumb, keep the size of the swap to be the double of your memory ram.

---

