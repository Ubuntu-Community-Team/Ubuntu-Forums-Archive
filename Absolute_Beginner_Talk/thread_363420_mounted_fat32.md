---
title: "mounted fat32"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by jtmedin on 2007-02-16
I have a hd with 2 partitions: hdb5 is the fat32 partition. I do a 'mount' & there it is. However, i am unable to see the directories & files. What more do i need to do? TIA
BTW the ntfs partition is hdb1, i can reference & that also show up with in the 'mount'

---

### Post by aysiu on 2007-02-16
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by taurus on 2007-02-16
What's the output of these two commands from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by jtmedin on 2007-02-17
ted@teds-tower:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9601    77120001    7  HPFS/NTFS
/dev/hdb2            9602        9729     1028160    f  W95 Ext'd (LBA)
/dev/hdb5            9602        9729     1028128+   b  W95 FAT32
ted@teds-tower:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              53G  2.2G   48G   5% /
varrun                760M   80K  760M   1% /var/run
varlock               760M  4.0K  760M   1% /var/lock
udev                  760M  160K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   19M  742M   3% /lib/modules/2.6.15-28-386/volatile
/dev/hdb5              74G   39G   36G  52% /media/windows
/dev/hdb1              74G   39G   36G  52% /media/windows
ted@teds-tower:~$

---

### Post by bodhi.zazen on 2007-02-17
Well, first problem is you have both hdb1 and hdb5 mounted at the same mount point, /media/windows.

Each partition should have a unique mount point when mounted.

Second, the link aysiu gave you will work.

Here is some additional information :

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

