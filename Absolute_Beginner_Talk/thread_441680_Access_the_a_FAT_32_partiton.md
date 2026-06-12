---
title: "Access the a FAT 32 partiton"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by BorgCymru on 2007-05-12
My 7.04 sees the FAT 32 partition and shows it on the desktop  but I have only 'read' access to it. Any idea how I can change the permission level so I can read and write to it ?

Thanks

---

### Post by taurus on 2007-05-12
How do you mount that fat32 partition?  Do you mount it from /etc/fstab or do you mount it by hand?

Post the output of these commands here.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by BorgCymru on 2007-05-12
It mounted itself


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/hda5            2551        3825    10241406   83  Linux
/dev/hda6            3826        5100    10241406   83  Linux
/dev/hda7            5101        5361     2096451   82  Linux swap / Solaris
/dev/hda8            5362        9729    35085928+   7  HPFS/NTFS

---

### Post by taurus on 2007-05-12
> **BorgCymru said:**
> It mounted itself


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/hda5            2551        3825    10241406   83  Linux
/dev/hda6            3826        5100    10241406   83  Linux
/dev/hda7            5101        5361     2096451   82  Linux swap / Solaris
/dev/hda8            5362        9729    35085928+   7  HPFS/NTFS

I don't see any fat32/vfat on the list.  Just in case you say /dev/hda2, it is only an extended partition and you cannot mount extended partition.  /dev/hda5, /dev/hda6, /dev/hda7, & /dev/hda8 are known as logical partitions under that extended partition.  

What does your /etc/fstab look like then?

```
cat /etc/fstab
```

---

### Post by BorgCymru on 2007-05-12
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda5 :
UUID=ca7719ab-01d3-4aa6-a401-7052f3026632 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 /home ext3 defaults 0 2
# Entry for /dev/hda1 :
UUID=1408F47508F456E8 /media/hda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hda8 :
UUID=8E68162368160A9B /media/hda8 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hda7 :
UUID=0f7949c8-9045-4675-b651-153ab3f6d403 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0


Yes the Ubuntu partitions and the 'shared' FAT32 partition are inside an extended partition and it wouldn't allow me to have all five partitions on one drive using the installer partition program

Part 1 = XP 
Part 2 = Ubuntu
Part 3 = /Home
Part 4 = Swap
Part 5 = 'Shared FAT32'

---

### Post by taurus on 2007-05-12
Can you please point me from this list which fat32 partition you want to mount?

```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 2550 20482843+ 7 HPFS/NTFS
/dev/hda2 2551 9729 57665317+ f W95 Ext'd (LBA)
/dev/hda5 2551 3825 10241406 83 Linux
/dev/hda6 3826 5100 10241406 83 Linux
/dev/hda7 5101 5361 2096451 82 Linux swap / Solaris
/dev/hda8 5362 9729 35085928+ 7 HPFS/NTFS

```
You already mounted both /dev/hda1 & /dev/hda8 with read-write, using ntfs-3g, from /etc/fstab.

The only partition is missing from your /etc/fstab is /dev/hda6 which is an ext3 filesystem.

---

### Post by BorgCymru on 2007-05-12
So why cant I do anything but read the 'SHARED' partition  ?

---

### Post by taurus on 2007-05-12
> **BorgCymru said:**
> So why cant I do anything but read the 'SHARED' partition  ?

What SHARED partition do you keep talking about?  Are you talking about /dev/hda6 or /dev/hda8?

```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 2550 20482843+ 7 HPFS/NTFS
/dev/hda2 2551 9729 57665317+ f W95 Ext'd (LBA)
/dev/hda5 2551 3825 10241406 83 Linux
**[COLOR="Red"]/dev/hda6 3826 5100 10241406 83 Linux[/COLOR]**
/dev/hda7 5101 5361 2096451 82 Linux swap / Solaris
**[COLOR="Red"]/dev/hda8 5362 9729 35085928+ 7 HPFS/NTFS[/COLOR]**

```

---

### Post by BorgCymru on 2007-05-13
OK I'm very new to this system

On my hard drive I have the follow partitions with these names

1 XP
[
2 Ubuntu
3 /Home
4/Swap
5 SHARED
]

All on IDE 0  80 gig HDD

XP is NTFS

all between the [  ] are on an extended partition.

SHARED is FAT 32

After a re boot I found I could now read and write to 'SHARED' but now I can't  write the the HDD that is connected as slave on IDE 1.

Thanks

trouble is I seem to have messed up my GFX drivers so can't even get into Ubuntu :(

---

### Post by taurus on 2007-05-13
> **BorgCymru said:**
> OK I'm very new to this system

On my hard drive I have the follow partitions with these names

1 XP
[
2 Ubuntu
3 /Home
4/Swap
5 SHARED
]

All on IDE 0  80 gig HDD

XP is NTFS

all between the [  ] are on an extended partition.

SHARED is FAT 32

After a re boot I found I could now read and write to 'SHARED' but now I can't  write the the HDD that is connected as slave on IDE 1.

Thanks

trouble is I seem to have messed up my GFX drivers so can't even get into Ubuntu :(

According to your outline above, SHARED is /dev/hda8 but sorry to tell you that /dev/hda8 is not fat32.  It is ntfs filesystem.

---

### Post by lneely on 2007-05-13
Just so you know, NTFS filesystems are read-only under Linux.  It is strongly discouraged, and disabled by default, to write to an NTFS partition.  (The only write support I've ever been able to use was "overwrite-only" anyway, so it's pretty limited...)

There are no FAT32 partitions.  The only thing closely /resembling/ a FAT32 partition is Win95 Extended, which I'm pretty sure isn't actually a FAT32 partition itself..

---

### Post by BorgCymru on 2007-05-13
I can assure you there IS a FAT 32 partition, I can see it now in XP.

I can also see it in Ubuntu and can now read and write to it. or could :)  I can also read and write to SOME of the NTFS partitions on the slave HDD.

As I said the 'permission' problem on the FAT 32 partition seems to have solved itself on a re boot, but alas I have borked my GFX driver and can't start Ubuntu now.

---

### Post by BorgCymru on 2007-05-13
MMM actually you are very right, sorry. I was looking through what was there and seeing what I though, again :)


OK I can access the NTFS drive that I thought was FAT32 /dev/hda8

The problem I have now is with my other 2 HDDs

one is in 2 partitions both as FAT 32,  EMPTY /dev/hdb1 and FOXTROT /dev/hdb2 now I can access read and write on FOXTROT /dev/hdb2 but not /dev/hdb1

and the other drive is NTFS   /dev/hdd1

Starting to get used to the Linux way of listing drives :) 

How can I set these up so they show on the desktop and I have full read write access please.

Some show owner as root some as my user name

Thanks


# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda5 :
UUID=ca7719ab-01d3-4aa6-a401-7052f3026632 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 /home ext3 defaults 0 2
# Entry for /dev/hda1 :
UUID=1408F47508F456E8 /media/hda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hda8 :
UUID=8E68162368160A9B /media/hda8 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/hda7 :
UUID=0f7949c8-9045-4675-b651-153ab3f6d403 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb1 /media/DRIVE_C ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/hdd1 /media/windows ntfs-fuse auto,gid=1001,umask=0002 0 0
#Added by diskmounter utility
/dev/hdb2 /media/hdb2 vfat rw,user,fmask=0111,dmask=0000 0 0

---

