---
title: "automounting NTFS as read-only"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Karsten.lundgaard.thomsen on 2008-03-24
Firstly I'm new to Linux. We have a harddrive with all our old documents. I would like to auto-mount this drive as read-only. Ubuntu recognise  the partition, but does not mount it on start-up. To mount it one need administration rights.

I have tried various version of fstab. But none of them are working.

After searching the forum I see that fdisk and blkid are needed to write the new line in fstab.

**sudo fdisk -lu**
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63     4096574     2048256   1b  Hidden W95 FAT32
/dev/hda2   *     4096575   156280319    76091872+   7  HPFS/NTFS

Disk /dev/hdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/hdb1              63   180715184    90357561    7  HPFS/NTFS**
/dev/hdb2   *   180715185   318649274    68967045   83  Linux
/dev/hdb3       318649275   321669494     1510110    5  Extended
/dev/hdb5       318649338   321669494     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 163.9 GB, 163927556096 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320171008 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   320143319   160071628+   7  HPFS/NTFS

```

**blkid /dev/hdb1**
```
/dev/hdb1: TYPE="ntfs" 
```

I think I'm missing a UUID here

Anyway the fstab looks like this, including my failed attempts:
** cat /etc/fs**tab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=6b93f313-1a23-4c67-bd52-8e74e238ce99 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=bc21a32d-d986-4d56-abec-23c598c7e4b9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# Mounting Document partition
#/dev/hdb1                       ntfs    
#/dev/hdb1       /media/Documents ntfs defaults 0 2
#/dev/hdb1                       ntfs defaults 0 2
#/dev/hdb1      /media/hdb1     ntfs    defaults        0       2
#/dev/hdb1      none            ntfs    defaults        0       2
/dev/hdb1       /media/hdb1     auto    r,auto,exec     0       0

```

---

### Post by kpkeerthi on 2008-03-24
What happens when you type ```
sudo mount -a
``` in a terminal?

* This will try to mount the entries in fstab without having to reboot. Post back with any errors it prints out.

---

### Post by kpkeerthi on 2008-03-24
Change the mount line in fstab as appropriate.
Make sure **/media/hdb1** exists. If not create using ```
sudo mkdir /media/hdb1
```

**Using the old NTFS driver:**
```
/dev/hdb1    /media/hdb1 ntfs  nls=utf8,umask=0222 0    0
```

**Using the new NTFS-3G driver:***
```
/dev/hdb1 /media/hdb1 ntfs-3g defaults 0 0
```

* Provides stable read/write support. Install it using ```
sudo aptitude install ntfs-3g
```

---

### Post by Karsten.lundgaard.thomsen on 2008-03-24
It is working.

Thanks

karsten

---

