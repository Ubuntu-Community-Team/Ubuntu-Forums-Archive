---
title: "Optical drive &quot;not mounted&quot; unless from boot-up"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-06-15
If I have a cd-rom which only works if the media is in the drive before the computer is booted. If I have an empty drive, load the cd media and try to read it, the Feisty says drive not mounted or some such cryptic message. What gives? Anybody know how to fix this?

---

### Post by Rocket2DMn on 2007-06-15
Have you checked your /etc/fstab file ?  Some recent updates have been screwing with people's mounting setups.
Cross check it with the output of
```
fdisk -l
```

---

### Post by Mark_in_Hollywood on 2007-06-15
mark@Lexington:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4772    38331058+  83  Linux
/dev/sda2            4773        4865      747022+   5  Extended
/dev/sda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1185     9518481   83  Linux
/dev/sdb2            1186        1240      441787+   5  Extended
/dev/sdb5            1186        1240      441756   82  Linux swap / Solaris

Disk /dev/sdc: 257 MB, 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         984      251888    e  W95 FAT16 (LBA)

Devices named /dev/sda and sdb are the two hard disks. Where OH! Where have my optical drives gone?

---

