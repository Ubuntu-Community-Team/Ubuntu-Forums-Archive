---
title: "Best Partition File System for Accessing on OSX &amp; Ubuntu?"
date: 2010-11-21
forum: Apple Hardware Users
---

### Post by -nat- on 2010-11-21
What would be the best file system to use on a partition that I want to be able to access (read/write) from both OSX (10.5.8 ) and Ubuntu (10.10)?
Also, I already have 4 partitions on my hard drive, and just wanted to check that adding a 5th, non-bootable one will work fine.

---

### Post by MisterGaribaldi on 2010-11-21
Here's an answer in two parts.

Part One:

Mac OS X recognizes and will read and write to Mac OS Standard (aka "HFS") and Mac OS Extended (aka "HFS Plus") partitions, and also Mac OS Extended Journaled (aka "HFS Plus Journaled"). It can read and write FAT16 and FAT32 and it can read from NTFS partitions. Assuming you install nothing else, that's the full extent of its native abilities.

If you install MacFUSE with NTFS 3G support, you will then be able to read and write NTFS partitions. There used to be another add-on which supported EXT2 and EXT3 partitions; however, I don't know if that is still a maintained app and I don't know how far forward compatible it is (i.e. I know it'll work in Tiger, but I don't know about Leopard or Snow Leopard).


Part Two:

Linux in general will recognize, read and write to FAT16/32, NTFS, EXT2/3/4, and a slew of other UNIX/Linux-environment partition types. If you install all the latest hfsprogs and such, you will be able to read and write Mac OS Standard and Mac OS Extended (that is, HFS and HFS Plus) but you will not be able to write to Mac OS Extended Journaled.

If you are dual-booting this system, there is a way (an expert on here can give guidance) to take your initially Mac OS Extended Journaled partition and turn off journaling, thus allowing your Linux install read and write access.


Hope this helps!

---

### Post by -nat- on 2010-11-21
Thanks for that very useful information MisterGaribaldi!

I had forgotten that it was only Journaled HFS that Linux couldn't write too, so I think I'll go with a non-Journaled HFS partition.

I've looked into the EXT2/3 Mac support add-on before, but decided not to install it after reading of it causing major data loss for some people.
I've also tried turning off Journaling on my OSX partition, but it made booting into Mac take ages.

---

