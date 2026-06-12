---
title: "best"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by Halsnalle on 2008-05-20
I installed Ubuntu 7.04 to try it out on my MacBook Pro (2nd gen, C2D) but I think I put it on a too small partition, because after having successfully upgraded to 8.04, my partition is now full, and I'm thinking about using Ubuntu more extensively, and perhaps switching permanently eventually...

Thus, two questions:

1. How best to resize the partitions? As I've understood it, these days you don't have to wipe clean to resize partitions, but I guess it's still a rather delicate task.

2. What would be the optimal partitioning of my 120 GB drive? From my rather unexperienced point of view, the best would be to have two minor partitions for the OS's respectively, and one for files, if I'm to switch between Mac and Ubuntu regularly.

---

### Post by volanin on 2008-05-20
Well, you don't say what's about your partition size, or anything else!
But before repartitioning, try this:

```
sudo aptitude clean
```

This will clean the installation packages downloaded by Ubuntu.
It's harmless and usually frees a lot of space.
See ya!
:)

---

### Post by ugm6hr on 2008-05-20
From Ubuntu, post the output from:
```
sudo fdisk -l
```

This will tell us what partitions you have at the moment.

The easiest way to resize partitions is with GParted (Partition Editor) from the Ubuntu LiveCD (or any other LiveCD with GParted); as you say, it does put your data at risk, so make sure you back-up everything first!

---

### Post by Halsnalle on 2008-05-21
Thank you both! Now, this is the output from fdisk:

> Disk /dev/sda: 120,0 GB, 120034123776 byte
255 huvuden, 63 sektorer/spår, 14593 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x00006b88

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26       13863   111149056   af  Okänd
/dev/sda3           13863       14532     5371094   83  Linux
/dev/sda4           14532       14594      495117+  82  Linux växling / Solaris


---

