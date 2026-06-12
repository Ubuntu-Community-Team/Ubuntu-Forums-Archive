---
title: "Partitoning structure 'up the creek'!"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-12-02
I have an issue and cannot fix it. I had XP as the first partition on the system with a dual boot. As I now use a Virtual Machine to run XP I deleted the XP partition,.I believe this caused a problem.

Gparted reports that I have 298.09 Gb of unallocated space (my entire 320Gb HDD).

fdisk-l reports:

Disk /dev/sda: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sda3               1       38913   312568641    5  Extended
/dev/sda4            2460       19031   133114590   83  Linux
/dev/sda5               1        2459    19751854+  83  Linux
/dev/sda6           38624       38913     2329393+  82  Linux swap / Solaris

I think sda1 is my problem, but is does not appear as a partition in fdisk for in fstab.

My plan is to copy my home partition (sda3) to an ext HDD, reformat and reinstall the OS and copy the home data back.

Problem - what are the commands to do this. I am familiar with the terminal, but not a pro. I am using a PCLOS livcd to write this as I cannot boot into my OS currently! When I plug my external HDD in it is not recognised.

help is greatly appreciated.

thcoklat

---

### Post by teryowen on 2007-12-02
Why not try out GParted and format SDA1 the unallocated space which is at the begining of the hard drive once the new partition tabel is written should be fine (back up your data before)

as for the copy command if you want to do what you want to do its:

```
cp -rv SOURCE TARGET
```
so for you:
```
cp -rv /home /media/yourexternalhd
```

-rv stands for r--> reclusive so to include sub folders and everything v--> verbose to show you what its copying you might want to remove the v if you dont want to see anything.

EDIT: i recommend only copying your home directory (well all the user files are) instead of the whole partition

---

### Post by tchoklat on 2007-12-02
> **teryowen said:**
> Why not try out GParted and format SDA1 the unallocated space which is at the begining of the hard drive once the new partition tabel is written should be fine (back up your data before)

as for the copy command if you want to do what you want to do its:

```
cp -rv SOURCE TARGET
```so for you:
```
cp -rv /home /media/yourexternalhd
```-rv stands for r--> reclusive so to include sub folders and everything v--> verbose to show you what its copying you might want to remove the v if you dont want to see anything.

EDIT: i recommend only copying your home directory (well all the user files are) instead of the whole partition


Sounds like the way to go. GParted does not show any partitions - part of the problem! Will this command affect permissions on the files I copy?

tchoklat

---

### Post by tchoklat on 2007-12-02
Can i do this graphically using <gksudo nautilus> and a simple cut and paste?

---

### Post by teryowen on 2007-12-02
it wont affect premission, and yes you can just do it using the GUI by copying and pasting as you wish.

---

### Post by tchoklat on 2007-12-03
done and AOK thanks dude!

---

### Post by teryowen on 2007-12-03
good stuff, if you can please mark this thread as solved under thread tools.

---

### Post by Dlaw2006 on 2007-12-05
I am having a similar problem, but not having to do with Windows necessarily. I am running a triple boot between PCLOS 2k7, Ubuntu and WinXP, and I want to delete the PCLOS partitions and resize my Ubuntu drive to take up the space it leaves. How would I go about that? I don't really want to reinstall Ubuntu again (I have been messing with the partition tables and, as a result, have had to reinstall probably 3 or 4 times), but if thats the only way, I guess I'll have to deal.

---

### Post by teryowen on 2007-12-05
boot of a live CD and use the partition manger to do this. i dont see a reason as to why it shouldnt work.

---

### Post by Dlaw2006 on 2007-12-06
I have tried that before, and when i go to boot it says its loading grub, then it gives some error, can't read MBR I think.

---

