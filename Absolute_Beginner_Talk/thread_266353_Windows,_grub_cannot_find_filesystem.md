---
title: "Windows, grub cannot find filesystem"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Kirky_D on 2006-09-27
This is my menu.lst entry for windows

```

title		Microsoft Windows
root	(hd0,1)
savedefault
makeactive
chainloader	+1
boot

```

After the recent kernal update my windows stopped booting, that is the entry which was put in by the update. 

When i try to boot into windows it says it cannot find the correct filesystem or something like that

Here is my fdisk -l

```

kirk@kirk-desktop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       24321   174875557+   f  W95 Ext'd (LBA)
/dev/sda5            2551       22380   159284443+   7  HPFS/NTFS
/dev/sda6           22381       24254    15052873+  83  Linux
/dev/sda7           24255       24321      538146   82  Linux swap / Solaris

```

Thanks for any help

---

### Post by Bachstelze on 2006-09-27
remove the *boot* line in your menu.lst

---

### Post by Kirky_D on 2006-09-27
Nope, same result unfortunately.

Cheers for the suggestion

---

### Post by Bachstelze on 2006-09-27
Windows is installed on /dev/sda1, right ? Not on /dev/sda5...

---

### Post by Kirky_D on 2006-09-27
99.9 % sure yea, Just to be sure though i will change it and try that

---

