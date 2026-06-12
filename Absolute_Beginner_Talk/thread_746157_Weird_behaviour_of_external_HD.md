---
title: "Weird behaviour of external HD"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by SleepyFloyd on 2008-04-05
Hello...

I got a problem with my external HD, a 500GB WD My Book. Every time a log on a new dummy of the drive is created. Don't know how to explain this properly, see the screenshot. Does anybody know how to solve this & what's causing this strange stuff?

I'm running the latest Hardy beta, which worked absolutly fine so far. The problem with the HD seems to be unrelated to any update I've installed.

---

### Post by Michael.Godawski on 2008-04-05
Wirklich merkwürdig... :)

Can you please post the output of 
```
sudo fdisk -l
cat /etc/fstab 
```

---

### Post by Victormd on 2008-04-05
> **Michael.Godawski said:**
> Wirklich merkwürdig... :)
what?? :D
... as we wait for the output...

---

### Post by Michael.Godawski on 2008-04-05
> what?? :)
Just guessing the OP can speak German. :)

---

### Post by SleepyFloyd on 2008-04-05
> **Michael.Godawski said:**
> Wirklich merkwürdig... :)

Can you please post the output of 
```
sudo fdisk -l
cat /etc/fstab 
```

Guessed right :)

>    Platte /dev/sda: 120.0 GByte, 120034123776 Byte
255 Köpfe, 63 Sektoren/Spuren, 14593 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xff58ff58

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       11035    88638606    7  HPFS/NTFS
/dev/sda2           11036       14544    28186042+  83  Linux
/dev/sda3           14545       14593      393592+   5  Erweiterte
/dev/sda5           14545       14593      393561   82  Linux Swap / Solaris

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xea31f151

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)



> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7d59383b-95c6-4559-9929-263e8c7d61db /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=61bb9472-7fad-42f1-a290-b1e4e7394d45 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


---

### Post by SleepyFloyd on 2008-04-05
No ideas? 

I also can't unmount the drive using any file manager, if that bit of information helps...

---

