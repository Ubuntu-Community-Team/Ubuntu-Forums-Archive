---
title: "Need Help to Unistall Mandriva"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by gecko113 on 2008-02-21
My hard drive does not pick the partions. I have Ubuntu and Mandriva installed and gparted is lieing to me. How do i uninstall Mandriva without accessing the partion at where it is located.

---

### Post by overdrank on 2008-02-21
> **gecko113 said:**
> My hard drive does not pick the partions. I have Ubuntu and Mandriva installed and gparted is lieing to me. How do i uninstall Mandriva without accessing the partion at where it is located.

HI and could you post a screen shot of gparted? Also can you post the output of the command ```
sudo fdisk -l

``` that is a small L

---

### Post by forestpixie on 2008-02-21
what lies are you being told exactly - and which gparted, the ubuntu version on the livecd, or in the install or a gparted livecd?

post the output of

sudo fdisk -l
cat /etc/fstab

I would assume that as long as the mandriva partition isn't being mounted you'll be able to do the partition work with ubuntu - if it is use the livecd - then delete the partition

if you installed mandriva after ubunut you'll probable need to reinstall grub - either use the ubunut livecd or get a copy of supergrub and boot with it

whatever you do - can you give people a bit more information, or it's just a whole bunch of guesswork

:)

---

### Post by gecko113 on 2008-02-21
Alrite sorry about that. Well i installed Ubuntu first and then mandriva second. I reinstalled the grub for me to be able to access Ubuntu. Well for the gparted part of it i used 2 different ones. I mean i used the one on the live disk of Ubuntu, and the one on Ubuntu installed on my harddrive and also i used the one i've burned on to a Cd. Once i run it. It tells me that my whole hard drive is all unallocated space.

---

### Post by gecko113 on 2008-02-21
I did as you said, cat /etc/fstab and the outcome that it is the following:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6f901977-aca0-48bf-a7e4-fb6eb243d9eb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=269a8653-8e09-4535-a9a0-87242f3f53eb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by forestpixie on 2008-02-21
can you do the fdsik -l we both asked for :)

---

### Post by gecko113 on 2008-02-21
When i type in sudo fdisk-l it tells me command not found

---

### Post by forestpixie on 2008-02-21
it's a lower case L and you need a gap

```
sudo fdisk -l
```

---

### Post by gecko113 on 2008-02-21
alrite here is the output for that:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sda2            5234       14455    74075715   83  Linux
/dev/sda3               1       14593   117218241    5  Extended
/dev/sda5               1        2550    20482812   83  Linux
/dev/sda6           14456       14593     1108453+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by gecko113 on 2008-02-21
Here is the screenshot of gparted

---

### Post by overdrank on 2008-02-21
> **gecko113 said:**
> Here is the screenshot of gparted

Ok is the screen shot from the live cd? And you can boot to ubuntu with out the live cd?

---

