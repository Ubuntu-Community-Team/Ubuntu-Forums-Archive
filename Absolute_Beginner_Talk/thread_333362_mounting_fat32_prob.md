---
title: "mounting fat32 prob"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-01-07
i put in fdisk -l and got :

> Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/hda2            2433        4764    18731790   83  Linux
/dev/hda3            4765        4868      835380    5  Extended
/dev/hda4            4869       19457   117186142+   b  W95 FAT32
/dev/hda5            4765        4868      835348+  82  Linux swap / Solaris

then i :

> sudo mount -t vfat /dev/hda4 /media/hda4
mount: wrong fs type, bad option, bad superblock on /dev/hda4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

i made the fat32 partition at ubuntu install time and cant use it, what is wrong here???

---

### Post by bodhi.zazen on 2007-01-07
My only thought is does your mount point exist ?

```
sudo mkdir /media/hda4
sudo mount /dev/hda4 /media/hda4
```

Permissions are another issue ....

---

### Post by antgul3382 on 2007-01-07
yeah it def does-0--the prob aint with the mount point its with the partittion itself????!!!!!!

---

### Post by bodhi.zazen on 2007-01-07
Looks that way ....

EDIT: Try re-formating the partition and then re-mounting it ...

---

### Post by antgul3382 on 2007-01-07
yeah i went in wndows and used partition magic 8 and its working now!

---

