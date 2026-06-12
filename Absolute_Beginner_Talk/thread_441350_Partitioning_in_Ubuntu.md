---
title: "Partitioning in Ubuntu"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-05-12
My current setup is an 80gig master drive with XP on it (one full partition), and a slave drive with Ubuntu Feisty, about 100gigs for / and 500mb swap partition. The problem is I do not see the rest of the free space when I boot up xp. The seagate drive (the slave) comes with partitioning software, but it says I have to delete the current partitions to make new ones, even though it shows the free space in the partition viewer. 

So, is there a way I can just format the free space on the drive so it will show up in My Computer, at which point I can reformat it to ntfs or whatever?

---

### Post by z1p101 on 2007-05-12
You can use fdisk in Linux. It seems scary but it's really pretty easy.
[http://www.linuxplanet.com/linuxplanet/tutorials/3174/6/](http://www.linuxplanet.com/linuxplanet/tutorials/3174/6/)

---

### Post by psusi on 2007-05-12
Free space does not show up in my computer; only partitions do.  More specifically, only partitions that windows recognizes do ( ntfs, fat ).  If you want windows to be able to use the unpartitioned space, then you need to make a partition there and format it as ntfs or fat.  You can do this in the windows disk administration utility or using gparted from the ubuntu livecd.

---

