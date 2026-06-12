---
title: "How to install OS X on a partition using gparted"
date: 2008-09-14
forum: Apple Hardware Users
---

### Post by rblakemesser on 2008-09-14
I'm using a MacBookPro1,2; Mac-F42DBEC8

I installed Hardy a few months ago, and just decided that I wanted to install os x on another partition.

Used gparted to create an unformatted partition (hfs+ option is grey).

I tried to boot the leopard install cd, but it wouldn't recognize any partitions.

Do I just need to format the second partition as hfs+, if so, how do I do that?

---

### Post by pxwpxw on 2008-09-14
macosx will only install to a guid partitioned disk. From the macosx dvd, the disk utility should show you the partitioning scheme you have, or use gparted in ubuntu.
You may have to re partition the drive.

---

### Post by rblakemesser on 2008-09-14
how do I run the disk utility off of the leopard dvd?

---

### Post by pxwpxw on 2008-09-14
I dont have leopard but tiger DVD gives you a menu bar up top, with disk utility somewhere.

---

### Post by cyberdork33 on 2008-09-15
It is the same on the Leopard DVD. What I would do is create free space, then use diskutility to create a new HFS+ partition for the install.

---

