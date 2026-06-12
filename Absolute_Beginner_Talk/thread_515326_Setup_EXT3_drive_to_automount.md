---
title: "Setup EXT3 drive to automount"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-08-01
I have an EXT3 drive that I formatted with Gparted.  It's 80 GB and I would like to know how to set it up to automount when I boot up the computer.  There are tons of guides for NTFS, but I have found nothing about EXT3.  Can anyone tell me how to setup an EXT3 drive to automount, through terminal or otherwise?

---

### Post by zidane2 on 2007-08-01
open gparted and the partion should be called /dev/sda3 or something like that, in a terminal type sudo gedit /etc/fstab

on a new line type 
<what it was called in gparted>    /media/HD    ext3  defaults,errors=remount-ro 0       1

you can replace HD at the end of /media/ to the name u want to give to the device

save and exit then in a terminal type sudo mkdir /media/HD (or whatever u named it)
then restart and it will automatically be mounted

---

### Post by Specter043 on 2007-08-01
I followed the steps to the letter, and it's not there. :/

---

### Post by zidane2 on 2007-08-01
paste the output of the command 
cat /etc/fstab
and i will try to help

---

### Post by Nythain on 2007-08-01
and the results of
sudo fdisk -l
and
blkid
would also be nice... then we can see what the device name is and get its uuid and give you the exact line to add or edit in your fstab

---

### Post by Specter043 on 2007-08-02
Sorry, was asleep.  The output of cat /etc/fstab is
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda1
UUID=3600917e-557d-446f-8ff1-090e05190355  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=257256a9-3987-4964-ac1d-4809335e6c1a  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto              0  0  
/dev/sdb1                                  /media          ext3         errors=remount-ro           0  0  
/dev/sdb/media/storage ext3 defaults,errors=remount-ro 0 1

the results of sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14576   117081688+  83  Linux
/dev/sda2           14577       14946     2972025    5  Extended
/dev/sda5           14577       14946     2971993+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291   83  Linux

and the results of blkid
/dev/sda1: UUID="3600917e-557d-446f-8ff1-090e05190355" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="257256a9-3987-4964-ac1d-4809335e6c1a" TYPE="swap" 
/dev/sdb1: UUID="467F-3DE7" TYPE="vfat" 

I think that was what everyone wanted.  BTW, My main HD is a 120 GB, which has a full Ubuntu install.

---

### Post by mjwhitfield on 2007-08-02
> **Specter043 said:**
> /dev/sdb/media/storage ext3 defaults,errors=remount-ro 0 1

You're missing a space between the device location and the mount location.  I'll try to explain what you're doing by adding that line, which is better than just copy and pasting :)

/dev/sdb is the device (aka what device am I mounting?)
/media/storage is the mount location (aka where am I mounting to?)
ext3 is the file system
defaults,errors=remount-ro 0 1 is voodoo magic

so it should look like:
```
/dev/sdb /media/storage ext3 defaults,errors=remount-ro 0 1
```

---

### Post by Specter043 on 2007-08-02
Wow, if that's all it was I feel kind of dumb.

---

### Post by Specter043 on 2007-08-02
Does anyone know how I can test to see if it worked?

---

### Post by Specter043 on 2007-08-02
Well, I think it worked, but it won't let me write to it.  Any ideas.

---

### Post by mjwhitfield on 2007-08-02
check the rights on /media/storage

who owns it?

---

### Post by Specter043 on 2007-08-02
Root.  Any way to change that so normal users can make folders in it/read and write to it?

---

### Post by Inxsible on 2007-08-02
```
sudo chown -R <your username>:<your group> <path to mount point>
```so assuming your user name to be specter
```
sudo chown -R specter:specter /media/storage
```

As an aside, why are you remounting the drive in fstab on errors? Does this drive have a Linux OS install?

If it is simply an EXT3 drive with no OS on it, the line in fstab should be

```
/dev/sdb1 /media/storage defaults 0 2
```

---

### Post by Specter043 on 2007-08-02
That's what someone earlier said.  I'll go change it.

---

### Post by Inxsible on 2007-08-02
>  /dev/sdb1                                  /media          ext3         errors=remount-ro           0  0  
/dev/sdb /media/storage ext3 defaults,errors=remount-ro 0 1

Something is wrong here...

How many partitions do you have on sdb ? 

if you have 2, then you need to mount /dev/sdb0 and /dev/sdb1. As of now, you are mounting sdb1 and sdb...which doesn't quite make sense !

---

### Post by Specter043 on 2007-08-02
Err...I'm not sure I understand, but sdb1 is 1 partition.  As far as I know it's just an empty 80 GB ext3.  Am I missing something?  Should I delete everything and try to restart the automounting process?

---

### Post by Specter043 on 2007-08-02
Any ideas?

---

