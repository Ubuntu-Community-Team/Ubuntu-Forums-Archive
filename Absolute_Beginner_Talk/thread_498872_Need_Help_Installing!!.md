---
title: "Need Help Installing!!"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Fr3sh103 on 2007-07-11
Hello everybody!!  Im new to the whole Linux stuff, so help would be nice!!

I need sum help installing Xubuntu.  When ever I try to install gpartition always says that i only have 8mb of space free when my hdd is 180gb and only 80gb is used by vista.  I downloaded and used gpartition to try to shrink the vista partition it always comes up with an error and will not let me do anything.  

If anybody has a solution it would be greatly appreciated!!

---

### Post by ramjet_1953 on 2007-07-11
Are you trying to change the partitions, while the disk is mounted?

If so, that is like trying to change the tyre on a car, while it is being driven!

The only way to partition a HDD is to do it while the drive is not mounted.

The best way to do it is to download the gparted iso and burn it as an iso to a CD. You then boot your system from that CD and you should be able to re-partition your HDD.

The link to download the gparted iso is here:

[http://www.gnu.org/software/parted/index.shtml](http://www.gnu.org/software/parted/index.shtml)

Don't forget to burn it as an iso image and to burn it SLOWLY, no faster than 4 X.

Regards,
Roger :cool:

---

### Post by p_quarles on 2007-07-11
Actually, gparted is not very friendly with Vista (and, no, I still don't know why exactly). The best thing to do is to use Vista's partition manager (it's in the Start menu under something like System Tools >> Disk Management). From there, you can right-click on the main partition and shrink it. 

Before you do this, though, you should defrag your hard drive.

After that, you can install *ubuntu. Just be sure to choose "use free space," and confirm that this free space matches the amount you freed up with the partition manager.

---

### Post by koshari on 2007-07-11
be VERY careful with the vista partition manager, its not very reliable, 

mine hosed my vista install.  like always bake sure you have a proven backup/restore strategy when attempting this kind of stuff.

---

### Post by dhughes on 2007-07-11
I also find with Gparted it can be frustrating when you see a partition and can't shrink it "to the left" only left to right.

---

### Post by Fr3sh103 on 2007-07-11
im back w/ bad news:(

i accidentaly wiped my vista so now im just installing xubuntu

so hopefuly it doesnt **** up yoo bad

---

