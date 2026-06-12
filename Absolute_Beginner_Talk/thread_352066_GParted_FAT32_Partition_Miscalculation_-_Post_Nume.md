---
title: "GParted FAT32 Partition Miscalculation? - Post Numero Uno"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Q.Tipperoo on 2007-02-02
Hi All.

First post after just soaking up info around this forum for a while.  After many Live CD memory installs, last week I finally started down the road of a permament install of 6.06 on a somewhat older IBM Aptiva with Windows 98 (not SE) on it.

My question is more of a 'anyone know why this is?' query from my first weekend's experiences.  Here's what I did:

GParted told me the used space on my windows FAT32 drive was 2.79 GiB.  So, using GParted I created a FAT32 partition on a USB hard-drive of 3.2 GiB, thinking that would be enough space.  (In have a cavern of unpartitioned space on that USB drive, so I could have gone bigger but I thought...why?)  Then I mounted all the required drives (so glad I can finally say I did that :) ), and used the cp command to copy the files from-to.

All was going well until the final 30 or so files it tried to copy...you guessed it...my USB partition was filled to the brim.

My question then, is why if 2.79 < 3.2 did I run into this issue?  A learned friend at work guessed perhaps unused block-space at the end of each file, which made sense to me, but I thought I would post and ask for a second thought about it.  Besides, I wanted to get that first bean!!!

(This weekend, 6.06 will be on that machine...after a partition size increase, I've already started cp round II.)

Happy to be learning.
JP

---

