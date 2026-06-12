---
title: "Mounting my data drive"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Mikasuliel on 2007-06-28
I reformated and did a clean install of Feisty. Was running Dapper. I installed a new data drive (the last one crashed).

Now when I booted it last night after installing the drive it found it as "disk" and i was able to access it, had to change permissions on it so I could read/write/etc on it.

Well I start the computer up today and Ubuntu doesn't even see the drive. So I figure I'll go into disk management and activate the volume, etc etc. I never had an issue with that in Dapper. Now I've noticed Disk Management is in a completely different place and it's giving me the error "There are no file systems which you are allowed to mount/unmount. Please contact  your administrator." It doesnt even give me the option to put the root password in. So I figured it was a permission error, so my user is in the root group and has that group as its primary group. It still won't let me do it. 

So my questions are 1. How do I get my drive to show up?  2. How do I get Disk Manager to work?

Thanks,
Mika

---

### Post by Inxsible on 2007-06-28
post your fdisk -l
 
and your etc/fstab
 
Is this an external drive ?

---

### Post by Mikasuliel on 2007-06-28
fdisk -l didnt show anything, this is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0480bb3-2a17-4904-bb22-03a3cfba208f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ef55b1ad-eacc-4ab7-82f7-9f79ce387049 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Mikasuliel on 2007-06-28
Internal 160gb Western Digital

---

### Post by Inxsible on 2007-06-28
> **Mikasuliel said:**
> fdisk -l didnt show anything
 
Did you do a ```
sudo fdisk -l
``` Also, whats the file format on the drive that you want to mount -- the 160GB WD

---

### Post by Mikasuliel on 2007-06-28
It's ext3


Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4866     1502077+   5  Extended
/dev/sda5            4680        4866     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

---

### Post by Inxsible on 2007-06-28
> **Mikasuliel said:**
> It's ext3
 
 
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 4679 37584036 83 Linux
/dev/sda2 4680 4866 1502077+ 5 Extended
/dev/sda5 4680 4866 1502046 82 Linux swap / Solaris
 
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
Device Boot Start End Blocks Id System
/dev/sdb1 1 19457 156288321 83 Linux
 
Open up your fstab
```
gksudo gedit /etc/fstab
```
 
Add this line to it
```
/dev/sdb1 /mnt/MyStorageDrive ext3 defaults 0 2
``` You can change the name of the mount point to anything you like for eg. /mnt/WD160 etc.
 
I normally mount internal drives under /mnt and external drives under /media. You can choose either or a completely new mount point.
Save the file and exit.
 
Then create the folder that you put in your fstab
```
sudo mkdir /mnt/MyStorageDrive
``` Of course, this name needs to be exactly same as the one you put in fstab.
Then do ```
sudo mount -a
```
 
That should be it

---

### Post by Mikasuliel on 2007-06-28
Thank you very much, I'll try it when I get home from work. I'll let you know how it goes.

---

### Post by Inxsible on 2007-06-28
> **Mikasuliel said:**
> Thank you very much, I'll try it when I get home from work. I'll let you know how it goes.
You are very welcome !

---

### Post by Mikasuliel on 2007-06-29
AWESOME! Thanks a TON! Worked like a charm!

---

