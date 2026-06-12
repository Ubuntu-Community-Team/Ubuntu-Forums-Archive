---
title: "Disk Maint"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by sterrac on 2005-11-05
On the 30th mount of my hard disk, ubuntu checked it for erorrs. I am assuming that it ran fsck or something like that. It reported that I had 1.6 percent non-contiguous files. What utlility do I use to correct that problem. I guess I need to defragment the hard drive.

Thanks for any help
Shane

---

### Post by gord on 2005-11-05
sudo apt-get install defrag

that should work for you fine, allthough im not sure wether it supports Ext3. 1.6 % non continous files doesn't sound so bad though, i don't think that it will hurt performance in any real way.

---

### Post by sterrac on 2005-11-05
I thank you for your help. 1.6 isn't bad, but it could become worse and I had no idea where to look. Thanks again
Shane

---

### Post by gord on 2005-11-05
linux isn't like windows, its very good at not getting fragmentated :) windows seems to enjoy it mind...

---

### Post by matthew on 2005-11-05
[quote=gord]sudo apt-get install defrag

that should work for you fine, allthough im not sure wether it supports Ext3.[/quote] Wait! I am almost certain that defrag does NOT support ext3. It's a pretty old program and last I heard it hadn't been updated in a long time simply because there really wasn't the need. I recommend you do a lot of web searching before you use it.

1.6% is nothing to worry about. If things get really bad the most common recommendation by linux/unix gurus is to copy the contents of the fragmented disk partition to an external disk or to another partition and then copy it back and it will then have no fragmentation. I have also been told that the time it takes to do this will be about 10x the amount of time saved due to slowed disk access caused by fragmentation--so unless you are approaching 10% fragmentation you really don't need to bother at all.

---

