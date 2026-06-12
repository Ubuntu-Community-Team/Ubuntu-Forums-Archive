---
title: "restore ubuntu after vista install"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-11-19
hey folks,
need some help with a minor mistake. I installed Vista the other day and, of course as expected of windows, it ran over the GRUB list (and now only shows vista and "older version of windows", no UBUNTU)...can someone offer some information about how to retrieve the grub please?

---

### Post by kpkeerthi on 2007-11-19
What is the output of 
```

sudo fdisk -l

```

---

### Post by pgar23 on 2007-11-19
> **kpkeerthi said:**
> What is the output of 
```

sudo fdisk -l

```

I can't use the command line because I can't even use ubuntu...I can't access it w/o the grub... :-(

---

### Post by kpkeerthi on 2007-11-19
Use your Live CD.

---

### Post by kpkeerthi on 2007-11-19
1. [Install GRUB ]("http://ubuntuforums.org/showpost.php?p=117829&postcount=2")to the partion where you have /boot mounted. 

2. Boot into Vista. Download and Install [EasyBCD]("http://neosmart.net/dl.php?id=1")

3. Follow the [instructions ]("http://neosmart.net/wiki/display/EBCD/Linux")to add GRUB to Vista Bootloader.

This has worked for me.

---

### Post by pgar23 on 2007-11-19
> **kpkeerthi said:**
> 1. [Install GRUB ]("http://ubuntuforums.org/showpost.php?p=117829&postcount=2")to the partion where you have /boot mounted. 
 
2. Boot into Vista. Download and Install [EasyBCD]("http://neosmart.net/dl.php?id=1")
 
3. Follow the [instructions ]("http://neosmart.net/wiki/display/EBCD/Linux")to add GRUB to Vista Bootloader.
 
This has worked for me.
 
Awesome...I will do that and also here is the result of sudo fdisk -l:
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 2804 22523098+ 7 HPFS/NTFS
/dev/sda2 2805 2891 698827+ 82 Linux swap / Solaris
/dev/sda3 11816 19457 61384365 83 Linux
/dev/sda4 2892 11815 71682030 f W95 Ext'd (LBA)
/dev/sda5 2892 11815 71681998+ 7 HPFS/NTFS
 
 
Partition table entries are not in disk order

---

### Post by pgar23 on 2007-11-19
since my /boot is on /dev/sda3 , how does that translate>? (hd0,2)? or something similar?

---

### Post by kpkeerthi on 2007-11-19
You are right.

---

