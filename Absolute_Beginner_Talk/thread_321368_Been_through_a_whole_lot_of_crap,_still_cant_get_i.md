---
title: "Been through a whole lot of crap, still cant get it"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by mickd1337 on 2006-12-18
Okay, Well i've had a lot of trouble trying to get this to work. I had a weird partition table and now have changed it slightly so i'll try get some help. At the moment nothing boots, Im trying to dual boot a previous installation of xp x64 with ubuntu, however all that splashes at the moment is the missing \system32\ntoskrnl.exe error. Luckily i have backed everything up, but dont really want to format that partition. The other partitions on that drive i put on ubuntu as a boot and swap drive. Here is the fdisk info:> Disk /dev/sda: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/hdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        5471    43945776    7  HPFS/NTFS
/dev/hdc2   *        5472        7051    12691350   83  Linux
/dev/hdc3            7052        7297     1975995    5  Extended
/dev/hdc5            7052        7297     1975963+  82  Linux swap / Solaris

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       12160    97675168+   7  HPFS/NTFS
/dev/hdd2           12161       14593    19543072+   f  W95 Ext'd (LBA)
/dev/hdd5           12161       14593    19543041    7  HPFS/NTFS


Anyone got any tips to get ubuntu to work? By the way i am installing v6.10 edgy eft, from live cd (i have alternate aswell).
Cheerz.](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by BarfBag on 2006-12-18
First off, we should try and get your Windows partition working again.  Have you tried booting your XP CD and repairing?

---

### Post by mickd1337 on 2006-12-18
I just installed 32bit vista over the top of xp x64, where vista now recognises that xp is still there for some reason. I am going to change over my primary and secondary cables for the ide drives to see if it works better with the ubuntu text install on the alternate cd.

---

### Post by pay on 2006-12-19
I didn't think that it was possible or recommended to install a 32bit installation over the op of a 64bit installation.

---

### Post by mickd1337 on 2006-12-20
Yeh as in formatted the partition, and installed 32bit vista, instead of x64, sorry for confusion.

---

