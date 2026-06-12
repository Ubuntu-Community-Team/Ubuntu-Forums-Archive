---
title: "Using Clean Hard Drive for Storage"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by cappii on 2007-09-24
Howdy from Texas.  I have recently uninstalled Windoze Vista from my Hard drive, leaving only Ubuntu.  I now have a nifty c. 50 Gb Partition that is just sitting there that I cannot access.  I used GParted to format it to ext3, however, the only option that I had was to create a second Primary partition.  I want t use this partition to store my music, odd programs for Windows that I use often (I am a computer Tech on the side of my regular job, and mostly deal with Windows and Macs, although I am trying to convert the world away from Microsoft :) )   Soooo.. if any of you can tell me what I did wrong, I would greatly appreciate it. :confused:

---

### Post by mendingo84 on 2007-09-24
it doesn't matter if it is a primary partition... you can store data on it. 
or do you have something else in mind? if that is so, could you please be more specific? ;)

---

### Post by logos34 on 2007-09-24
Sounds like an ext3 primary partition is exactly what you want.  If you ever need to access it from windows, however, you'll need fs-driver so windows can read and write to it.

---

### Post by cappii on 2007-09-24
Well, specifically :| I have formatted this as an ext3, and cannot access it from my current Ubuntu desktop.  I have to go into GParted to even see it.  How can I access this drive to use as a storage medium?  When I navigate to Places>Computer  the only choices I see are Filesystem and CD/rw - DVD/+-RW Drive...  no other partition.

---

### Post by Seisen on 2007-09-24
Once you boot into Ubuntu you should be able to mount the partition that might be why you can't access it.

---

### Post by mendingo84 on 2007-09-24
please paste the result of this command ( in a Terminal ) back:

```
sudo fdisk -l
```

---

### Post by vanadium on 2007-09-24
Indeed Ubuntu will only detect and setup partitions on non-removable drives the first time you install it. If you add or change non-removable partitions later, then you need to configure Ubuntu manually to mount the partition automatically.

This is done by editing /etc/fstab. Because the line for your Windows partition will still be in /etc/fstab, you will just be able to edit that one to reflect the changes (i.e. ext3 instead of ntfs). If you post the output of "sudo fdisk -l" here, people will already be able to brew an fstab line for you. I advice you also to post your current /etc/fstab, so we can say precisely what you need to edit there.

---

### Post by cappii on 2007-09-24
The Results from the Sudo fdisk -l is as follows:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6319    50757336   83  Linux
/dev/sda3            6320       11916    44957902+  83  Linux
/dev/sda4           11917       12161     1967962+   5  Extended
/dev/sda5           11917       12161     1967931   82  Linux swap / Solaris

The etc/fstab reads:

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=3bd0646e-53f4-41d7-8519-bff72fb02c61 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=c4d531b1-12ca-4818-a262-3376682f12db none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by mendingo84 on 2007-09-24
if i am figuring things out correctly, than sda4 is the partition we are talking about. if that is so, you should add this entry in your /etc/fstab :

```
/dev/hdb5 /media/sda4 ext3 defaults,errors=remount-ro 0 1
```

create the directory /media/sda4
and then :
```
mount -a
```

---

### Post by cappii on 2007-09-24
I think that it is SDA1, the former windows partition, actually....  I no longer have Windows, so that is only my assumption, however.

---

### Post by mendingo84 on 2007-09-24
yes, it is **sda1**, sorry. however, the steps are the same, just replace sda4 with sda1
oh, and a little change, make the entry in the fstab look like:
```
/dev/sda1 /media/sda1 ext3 defaults 0 0
```

---

### Post by cappii on 2007-09-27
Sorry for taking so long to reply.  I did edit the fstab as you suggested, however, sudo mount -a is suggesting that there is nothing to mount.

---

### Post by logos34 on 2007-09-27
> **cappii said:**
> Sorry for taking so long to reply.  I did edit the fstab as you suggested, however, sudo mount -a is suggesting that there is nothing to mount.

You need to create the mount point:
[B]
sudo mkdir /media/sda1[/B]

---

### Post by cappii on 2007-09-28
That did it, Thanks!!  Now how do I mark this solved??? :guitar:

---

