---
title: "partition problem fat32 to ext2"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by jensenhearing on 2006-09-23
Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+    716     717-   5759271    c  W95 FAT32 (LBA)
/dev/hda2       1219    2490    1272   10217340    f  W95 Ext'd (LBA)
/dev/hda3        717    1218     502    4032315   83  Linux
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5       1869+   2490     622-   4996183+   b  W95 FAT32
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/hda6       1219+   1245      27-    216814+  82  Linux swap / Solaris


Have read about mounting and unmounting and so on but still cannot get my hda5 to work so used sfdisk -l and got this output. This is a dual boot PC with Win98SE on C drive. The hda5 which is a fat32 no longer shows up when running win98SE and cannot mount hda5 in ubuntu either.

What should i do to change the fat32 to ext2 so that i can use it as a partition in ubuntu? tried using sudo rm /dev/hda5 but nothing happened. Tried to go to DOS to use fdisk to remove partition 5 (formerly known as drive D in windows) but DOS won't work just hangs the PC.

Thanks for help in advance.

---

### Post by jorn on 2006-09-23
Take a look at the application "gParted". It's in "Packet manager".
It will do the filesytem change for you.
After that you will have to edit the file "fstab" in order to make the partition visible for you.

---

### Post by jensenhearing on 2006-09-23
```

(parted) print
Disk geometry for /dev/hda: 0.000-19541.320 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031   5624.318  primary   fat32       boot, lba
3       5624.319   9562.126  primary   ext3
2       9562.126  19539.997  extended              lba
6       9562.188   9773.920  logical   linux-swap
5      14660.912  19539.997  logical   fat32

```

Does this extra info help? Am having problem mounting MINOR 5 and cannot change MINOR 5 from fat32 to ext3 (not sure which to use)

Tried changing it via system -> Administration -> Disks Manager -> Partition Fiel System and click on format and change the selection from fat32 to ext2 but that did not work. Now partition 6 shows up as FREE space that is not paritioned but the bottom bar says - FREE SPACE not available.

---

### Post by YeahBuntu on 2006-09-23
Is this a physical seperate drive?  It appears to be.  Grab a copy of GWSCAN (its what I use) and wipe the drive.  Then use Gparted to repartition and format.

---

### Post by jorn on 2006-09-23
Go>System>Administration>Synaptic Packetmanager.
Search for "gParted".
Install it. or
Type in terminal:
> sudo apt-get install gparted 
That command will install it for you.
You need this program to change filesystems or for repartitioning.

---

