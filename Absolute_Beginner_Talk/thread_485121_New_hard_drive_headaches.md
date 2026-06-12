---
title: "New hard drive headaches"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by begbie on 2007-06-26
I have a new 250gb hard drive, it is set to slave.
entering:         sudo fdisk -l
returns:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4681    37600101   83  Linux
/dev/sda2            4682        4865     1477980    5  Extended
/dev/sda5            4682        4865     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Why do the ide drives show up as sda and sdb?

Entering:     fdisk /dev/sdb
Returns:
Unable to open /dev/sdb

Am I missing something?  Do I need gparted?

---

### Post by Inxsible on 2007-06-26
> **begbie said:**
> I have a new 250gb hard drive, it is set to slave.
entering: sudo fdisk -l
returns:
 
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 4681 37600101 83 Linux
/dev/sda2 4682 4865 1477980 5 Extended
/dev/sda5 4682 4865 1477948+ 82 Linux swap / Solaris
 
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
Device Boot Start End Blocks Id System
 
Why do the ide drives show up as sda and sdb?
 
Entering: fdisk /dev/sdb
Returns:
Unable to open /dev/sdb
 
Am I missing something? Do I need gparted?
 
So whats the problem again? sda sdb is the naming convention of how the kernel names devices. The syntax is *dX?, where * = s or h, X = a,b,c..... , and ? = 1,2,3,4......
s = sata drives
h = ide drives
a = 1st drive
b = 2nd drive...and so on
 
They will also be followed by numbers for the partitions they have on it (if any)
 
sda1, sda2.....sdb1 sdb2...etc
 
The newest kernel in Ubuntu --2.6.20-16 i think, recognizes all the drives as sata. Do not worry, it does not impede the functionality of any.

---

### Post by ugm6hr on 2007-06-26
My IDE drive is sda too.  Doesn't change the fact that it works.

Your new drive appears to be unpartitioned / unformatted.  

GParted should make sorting this out for you easy.  Or *sudo cfdisk* if you don't want GParted.

---

### Post by Inxsible on 2007-06-26
fdisk is giving you problems because you are not using any partition number to fdisk on.
 
Your sdb seems to be just a lot of unallocated space without any file system on it.

---

### Post by begbie on 2007-06-26
Then I won't worry that my ide drives show up as sata.

Do I have to install gparted?
Is there an advantage to using Gparted over cfdisk?
When I enter  sudo cfdisk sdb
I get:
 FATAL ERROR: Cannot open disk drive
thanks for quick responses.

---

### Post by Inxsible on 2007-06-26
> **begbie said:**
> Then I won't worry that my ide drives show up as sata.
 
Do I have to install gparted?
Is there an advantage to using Gparted over cfdisk?
When I enter sudo cfdisk sdb
I get:
FATAL ERROR: Cannot open disk drive
thanks for quick responses.
 
GParted will give you a nice GUI to work with. The LiveCD, if you still have it has GParted on it. You can use that to partition/format you drive.

---

### Post by begbie on 2007-06-26
Sounds good, thanks.
I entered:  sudo apt-get install gparted
EDIT: found it

---

