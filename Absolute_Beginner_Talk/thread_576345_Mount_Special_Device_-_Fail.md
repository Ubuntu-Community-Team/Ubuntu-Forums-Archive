---
title: "Mount Special Device - Fail"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-10-15
I see this message when the system loads.

> Mount Special Device /dev/disk/by-uuid/ 6037-1309 does not exist.  Fail.

Fstab shows that this relates to sda5.  I also had a look with fdisk -l

Any suggestions what I should do to zap this?

```

sudo fdisk -l



Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)

/dev/sda2            2551        2805     2048287+  82  Linux swap / Solaris

/dev/sda3            2806        9052    50179027+  83  Linux

/dev/sda4            9053        9729     5438002+   f  W95 Ext'd (LBA)

/dev/sda5            9053        9729     5437971   83  Linux


```

```

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda3

UUID=04d21ba6-4089-445f-a133-419a233192d6 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1

UUID=4633-70ED  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda5

UUID=6037-1309  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sdb1

UUID=b2160c1c-39f3-4e6d-8558-2d812637ffa8 /media/sdb1     ext3    defaults        0       2

# /dev/sdb5

UUID=89ab345e-e81f-420b-99a4-1f8425aac7d4 /media/sdb5     ext3    defaults        0       2

# /dev/sdb6

UUID=8BED-3CDA  /media/sdb6     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sdb7

UUID=45F7-E48F  /media/sdb7     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sdc1

UUID=45F6-9E39  /media/sdc1     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sdc5

UUID=ec66d5a7-4707-4956-8488-df4396240ee7 /media/sdc5     ext3    defaults        0       2

# /dev/sda2

UUID=10d58452-8e78-4087-8507-cbd959cd760d none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---

### Post by anaconda on 2007-10-15
My guess is that you have formatted that partition recently and when you reformat a partition the uuid of that partition changes. So you cant mount it anymore with the old uuid.

Type in terminal:
```
ls -la /dev/disk/by-uuid/
```
and check that the uuids match with those in your /etc/fstab -file.

---

### Post by realvz on 2007-10-15
are you using Gutsy?
if so goto synaptics and try reinstalling HAL...
and see if it auto mounts

---

### Post by expatCM on 2007-10-15
Yes, you are correct, I reformatted the partition a couple of weeks ago.

I ran the command but I do not know how to relate the result to the partition.... I cannot see sda5 in the list...

```
 ls -la /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 220 2007-10-16 00:43 .
drwxr-xr-x 6 root root 120 2007-10-16 00:43 ..
lrwxrwxrwx 1 root root  10 2007-10-16 00:43 04d21ba6-4089-445f-a133-419a233192d6 -> ../../sda3
lrwxrwxrwx 1 root root  10 2007-10-16 00:43 10d58452-8e78-4087-8507-cbd959cd760d -> ../../sda2
lrwxrwxrwx 1 root root  10 2007-10-16 00:43 45F6-9E39 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2007-10-16 00:43 45F7-E48F -> ../../sdb7
lrwxrwxrwx 1 root root  10 2007-10-16 00:43 4633-70ED -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-10-16 00:43 89ab345e-e81f-420b-99a4-1f8425aac7d4 -> ../../sdb5
lrwxrwxrwx 1 root root  10 2007-10-16 00:43 8BED-3CDA -> ../../sdb6
lrwxrwxrwx 1 root root  10 2007-10-16 00:43 b2160c1c-39f3-4e6d-8558-2d812637ffa8 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2007-10-16 00:43 ec66d5a7-4707-4956-8488-df4396240ee7 -> ../../sdc5
```


No this is not Gutsy ... not until later in the week :)

---

### Post by anaconda on 2007-10-15
Hmm.. I thought that command should list all uuid:s.. or was it just uuids of mounted partitions?

Anyway. you dont have to use uuid:s just change the uuid back to old style  in your fstab eg.
/dev/sda5
instead of uuid. That should fix things.

---

### Post by expatCM on 2007-10-16
I have had a look at what uuid means and see that it is similar to a mac address.   

So what you are saying it to edit fstab to remove all uuid information and just leave the path to the drive.  Easy.

Do you happen to know why this information appears in the first place and what is it used for by Ubuntu since if the system will work by simply editing it out then there seems to be little value by having it there in the first place?

---

### Post by anaconda on 2007-10-16
> **expatCM said:**
> I have had a look at what uuid means and see that it is similar to a mac address.   

So what you are saying it to edit fstab to remove all uuid information and just leave the path to the drive.  Easy.

Do you happen to know why this information appears in the first place and what is it used for by Ubuntu since if the system will work by simply editing it out then there seems to be little value by having it there in the first place?

I think it has something to do with multiple hard drives. Eg. if you switch the order of your hd:s then the sda, sdb, sdc naming would change. The uuid:s are unique to that specific partition. The problem with uuid:s is that it changes when you format the partition, and they look horrible. A formatting tool which would keep the old uuid would be handy.

Never had problems with the /dev/sda1 style of assigning hd:s

And no need to remove ALL uuid information from fstab. Just the ones you have problems with. and maybe the swap partition (which gets formatted most often. eg. when installing another linux on a separate partition.)

---

### Post by expatCM on 2007-10-16
In case it is of interest to anyone, it seems that the uuid's which are used on a system may be identified with the following command - 

blkid

---

