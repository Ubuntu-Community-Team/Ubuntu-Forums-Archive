---
title: "Partitioning ?"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-07-22
Ok,I wanted to set up another partition for data,music,etc. I accomplished this by using GParted to shrink my orginal partition (hdb1)to 20G and making another partition (hdb3) to 35G. I can't see this new partition anywhere in the filesyatem,and I get this now:

drakkor@drakkor:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1431    11494476    7  HPFS/NTFS
/dev/hda2            1432        9732    66677782+   f  W95 Ext'd (LBA)
/dev/hda5            1432        5861    35583943+   7  HPFS/NTFS
/dev/hda6            5862        9732    31093776    7  HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2631    21133476   83  Linux
/dev/hdb2            7113        7299     1502077+   f  W95 Ext'd (LBA)
/dev/hdb3            2632        7112    35993632+  83  Linux
/dev/hdb5            7113        7299     1502046   82  Linux swap / Solaris

Partition table entries are not in disk order
drakkor@drakkor:~$

---

### Post by taurus on 2006-07-22
After you resized it, did you format and mount it, /dev/hdb3?

---

### Post by philippe_carlo on 2006-07-22
You need to mount it.
```

sudo mkdir /media/data
sudo mount -t ext3 /dev/hdb3 /media/data

```

You can automate this as follows
```
sudo gedit /etc/fstab
```
Add the line
```
/dev/hdb3       /media/data  ext3    rw,user,auto  0       0
```

---

### Post by Drakkor on 2006-07-22
Thanks for the replies,I have mounted it,but still don't know where to find it ?  :confused:  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /media/data     ext3    rw,user,auto    0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /windows3       ntfs    nls=utf8,umask=0222        0       0
/dev/hda7       /windows4       ntfs    nls=utf8,umask=0222        0       0

---

### Post by taurus on 2006-07-22
> **Drakkor said:**
> Thanks for the replies,I have mounted it,but still don't know where to find it ?  :confused:  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /media/data     ext3    rw,user,auto    0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /windows3       ntfs    nls=utf8,umask=0222        0       0
/dev/hda7       /windows4       ntfs    nls=utf8,umask=0222        0       0

How about in /media/data!!!  :rolleyes:

---

### Post by philippe_carlo on 2006-07-22
The files on the partition are now in the folder /media/data.

---

### Post by Drakkor on 2006-07-22
Please excuse my denseness,lol

---

### Post by Drakkor on 2006-07-22
Nevermind,I didn't make the folder "sudo mkdir /media/data
sudo mount -t ext3 /dev/hdb3 /media/data" 
I just skipped down to the "automated" part ! :oops: 
Thanks guys ! Cheers :)

---

### Post by taurus on 2006-07-22
After you edited your /etc/fstab to include /dev/hda3 (/media/data), did you mount the whole thing again with

```

sudo mount -a

```
If you didn't run the above command, run it now and see if there is a /media/data.  Otherwise, run this instead.

```

sudo mount -t ext3 /dev/hda3 /media/data
df -h

```

---

### Post by Drakkor on 2006-07-22
Thx,taurus,but see above post :)

---

### Post by taurus on 2006-07-22
> **Drakkor said:**
> Thx,taurus,but see above post :)

Yip.  I know.  I guess everything is good for you now.  ;)

---

### Post by Drakkor on 2006-07-22
Yep,GParted is actually quite nice,first time I used it,I also have to re-edit the fstab to remove a deleted windows partition,lol.Thanks for the help ! :p

---

