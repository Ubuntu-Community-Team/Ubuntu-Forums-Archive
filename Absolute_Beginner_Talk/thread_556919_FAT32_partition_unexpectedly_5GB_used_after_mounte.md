---
title: "FAT32 partition unexpectedly 5GB used after mounted"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by jfehribach on 2007-09-21
I have an 11GB FAT32 partition shared by Ubuntu and Win2000 on a 40GB disk.  That partition (under Ubuntu) also gets mapped from a WinXP machine on my home network.  I installed Ubuntu and set this all up about a month ago, and I mistakenly declared "Mission Accomplished".  I just noticed from the XP PC that the drive was almost full.  So I moved everything off that partition.  Win2000 says the partition has 11GB available.  Ubuntu says 5GB used and 6 GB available,  Running 'gparted' utility, there are 5 lines reported for my 40GB disk:
1.  /dev/hda1; fat32;;Size 12.11GiB Used 4.85 GiB; Unused 7.26 GiB; Flags boot lba
2.  /dev/hda2; extended;; 11.85GiB;;;;lba
3.  (indented) /dev/hda5; fat32; Mountpoint /media/Fdrive; 11.18 GiB; 5.09 GiB; 6.09 GiB;
4.  (indented) /dev/hda6; linux-swap;; 690 MiB;;;;
5.  /dev/hda3; ext3; /; 14.32 GiB 4.12 GiB;10.21 GiB;

If I use 'gparted' and select line 3 , then Partition ... unmount, the Used becomes 11.21 MiB and the Unused becomes 11.17Gib.  Doing  Partition ... mount on ... /media/Fdrive causes the numbers to revert to Used 5.09 GiB; Unused 6.09 GiB;

Mounting my FAT32 partition costs me 5 GB.  Not acceptable!  What's going on?

I'd prefer an answer that returns my 5 GB, but any insightful answer would be welcomed.

Thanks.
Jerry Fehribach

---

### Post by eph1973 on 2007-09-22
I believe your problem lies in the way FAT32 works as far as allocating storage area.  After your drive gets so big with FAT32 it becomes more and more inefficient as far as allocating the drive.  That's the reason why people made partitions when their drive got above something like 8GB, because much bigger than that, and you start throwing away storage (as you see).  When XP came out, NTFS handled large drives a lot better and it wasn't as much of a problem.  If you were to change that FAT32 partition to FAT16, the used/unused would get even smaller.  If you broke your FAT32 partition down into, say 3 7GB partitions, you should see a much more efficient use of your FAT32 partition.

---

