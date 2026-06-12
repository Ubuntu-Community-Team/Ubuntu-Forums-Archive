---
title: "[SOLVED] How to install PC BSD?"
date: 2008-09-12
forum: BSD
---

### Post by Canis familiaris on 2008-09-12
My partition Table is like this: (O/P of sudo fdisk -l)


```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ded11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4802    38572033+  83  Linux
/dev/sda2   *       29092       30401    10522575   bf  Solaris
/dev/sda3            4803        7003    17679532+   7  HPFS/NTFS
/dev/sda4            7004       29091   177421860    5  Extended
/dev/sda5            7004       15473    68035243+  83  Linux
/dev/sda6           15474       22613    57345423+   7  HPFS/NTFS
/dev/sda7           23888       29091    41799680    7  HPFS/NTFS
/dev/sda8           22614       22935     2586433+  82  Linux swap / Solaris

Partition table entries are not in disk order
```
I have free space of 7.29 GB as additional space. However the PC BSD installer is confusing for me and I am unable to figure how to set up the partition. Do I have to allocate a Primary Partition for PC BSD like I had to for Solaris?

---

### Post by cardinals_fan on 2008-09-12
I remember the installer as pretty easy... could you post a screenshot of the stage that confuses you?

---

### Post by Canis familiaris on 2008-09-12
The installer seems easy but due to my lack of experience. I'm unable to figure out the partitioning part which is leaving me confused.
Sadly, I can't post the screenshot now because:
(1) I'm trying to install it physically and I dont know How to post screenshot while doing it. Maybe guide me on this regard?
(2) I downloaded the AMD64bit version and Virtualbox can't run it.
(3) It would be tedious for me to run KVM and then take the screenshot. (KVM's bit tricky)

---

### Post by cardinals_fan on 2008-09-12
> **Anurag_panda said:**
> The installer seems easy but due to my lack of experience. I'm unable to figure out the partitioning part which is leaving me confused.
Sadly, I can't post the screenshot now because:
(1) I'm trying to install it physically and I dont know How to post screenshot while doing it. Maybe guide me on this regard?
(2) I downloaded the AMD64bit version and Virtualbox can't run it.
(3) It would be tedious for me to run KVM and then take the screenshot. (KVM's bit tricky)
Sorry, I'm mixed up.  If you have a camera, you could take a pic of your screen.  Otherwise, just explain what's confusing in detail.

---

### Post by Canis familiaris on 2008-09-12
> **cardinals_fan said:**
> Sorry, I'm mixed up.  If you have a camera, you could take a pic of your screen. 
I have lost the USB Cord of the Camera. I can take pictures but not post them :lol:

>  Otherwise, just explain what's confusing in detail.


Thanks. I'll restart and come back.

---

### Post by Canis familiaris on 2008-09-13
When the Wizard Reaches:
Drive Selection:

It lists Detected HD:

```
/dev/ad0  <name of the HD>
```

When the HD is selected:
It lists three partitions:
```
/dev/ad0s1    37668MB   Linux Native
/dev/ad0s2    10275MB   Solaris (x86)
/dev/ad0s3    17265MB   (OS2/HPFS....)

```

When one of the partitions is selected, then it lists in the next page:```

/dev/ad0s2a      /            16753MB      UFS
/dev/ad0s2b      SWAP         512MB        SWAP
```

It doesn't list the logical drive and I want to install PC BSD in the logical drive. Is it possible?

---

### Post by Sorivenul on 2008-09-13
Per the PC-BSD [Quick Guide]("http://docs.pcbsd.org/guide/chap2.3.html"):
> Trying to install on a logical partition will convert your extended partition into a primary partition and erase all logical partitions of your system.

---

### Post by Canis familiaris on 2008-09-13
So I have to Remove Windows. 

Goodbye Windows.

---

### Post by Sorivenul on 2008-09-13
Don't.  Not yet anyway.  If I remember correctly the installer also REMOVES any extended partitioning you currently have.  Definitely do a backup.  Will try to find the details.

EDIT: False alarm.  Just bad memory of what I've already read.  You should be fine.  Good luck in the PC-BSD adventure!

---

### Post by Canis familiaris on 2008-09-13
Typing from PC-BSD. Seems pretty nice. I suppose I made a mistake of downloading and installing the 64bit version. Can't install Opera, yet.
Out of box Flash, Multimedia is nice too. The KDE 3.5 in this Edison Edition is Fine too.

Just Restarting to Check Whether Linux is Fine and then I'll mark this as solved.

EDIT: It's Fine. :)

Now I have to figure How to add PC-BSD to my GRUB menu.

EDIT: PC-BSD has been added to my GRUB menu. To those interested, I added the following lines:

```
#BSD
title	PC-BSD 1.5.1
root	(hd0,2)
chainloader	+1
makeactive
boot
```

where (hd0,X-1) = /dev/sdaX

---

