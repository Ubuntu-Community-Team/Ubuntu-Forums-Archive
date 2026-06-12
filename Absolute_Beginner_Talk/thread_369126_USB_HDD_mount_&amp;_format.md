---
title: "USB HDD mount &amp; format"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by AustinJM on 2007-02-24
I installed Ubuntu a couple weeks ago (dual boot w/WinXP Pro).  So far, I like it.

I installed KDE, so now I have Kubuntu.  How do I go back to just regular Gnome/Ubuntu?


I have a 250gb hard disk in a SATA/USB external enclosure.  There is no data of consequence on the disk.  The disk has recently been formatted with NTFS, however right now the formatting & partitions are removed...  it's just ~250gb of unallocated space.

I would like to partition (90/160) and format the disk with HFS+ on the 90gb partition and FAT32 on the 160gb partition.  The end goal is to be able to transfer ~80gb of music files between a Vista PC, a MacBook (OS X) and the Ubuntu machine.

How do I get Ubuntu to detect the drive?  How do I go about formatting the FAT32 partition?  Would it be better to partition the drive with a particular OS?

I realize that I can format up to a 32gb partition with FAT32 in Windows, but I want larger partitions.

Thanks.:popcorn:

---

### Post by george29 on 2007-02-24
use gparted to format the partitions. you can install it using synaptic if you don't  already have it installed.

ubuntu should just autodetect the drive..

---

### Post by AustinJM on 2007-02-24
I realize Ubuntu should just autodetect the drive, however that's not happening.

I've connected the drive as a sigle 250gb storage device (unallocated), and I've connected the drive as a single 250gb partitioned (raw) device.  No luck.

---

### Post by robophred on 2007-02-24
What brand is the external drive?  I have a MyBook that works out of the box.  It has both usb and firewire support (I use firewire).  It shows up under places->computer, with the firewire emblum in the upper-right of the basic hard drive icon.

---

### Post by AustinJM on 2007-02-25
The drive is a Western Digital, and the external case is a Rosewill.

I was able to use gparted to format one partition as FAT32, and then the MacBook formatted the other partition to HFS+ with no problem.

I'd like to use EXT2 instead of FAT32, so that I get the benefit of the better file system & am able to go between PC, Ubuntu & Mac.  There are drivers which allow WinXP and Mac OS X to read EXT2, however I can't find anything which allows Windows Vista to read EXT2...  Anybody know of something for Vista?

---

