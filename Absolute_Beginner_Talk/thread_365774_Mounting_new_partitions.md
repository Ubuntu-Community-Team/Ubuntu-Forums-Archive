---
title: "Mounting new partitions"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by noenter1 on 2007-02-20
Ok i have 2 new partitions i want to mount one is a ext3 partition the other is a windows partition.

```
$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20022   160826683+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       12752       29683   136006290   83  Linux
/dev/sdb2           29684       30401     5767335    5  Extended
/dev/sdb3               1       12751   102422376   83  Linux
/dev/sdb5           29684       30401     5767303+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

an this is my /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1     /media/windows    ntfs-3g       auto,gid=1001,umask=0000       0       0
# /dev/sdb1
UUID=905a859d-ee8a-428a-9812-eae973deaf5a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=9567-4287  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=ce40d503-2e61-46f1-af04-68f876547b3a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

The windows partition is sda1 and the ext3 partition is sdb3. I have already tried using this giude for mounting windows and it didnt work [http://www.ubuntuforums.org/showthread.php?t=328627&highlight=mounting+windows+ntfs+partition](http://www.ubuntuforums.org/showthread.php?t=328627&highlight=mounting+windows+ntfs+partition)
Can anyone help me please?

---

### Post by aysiu on 2007-02-20
These links should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by noenter1 on 2007-02-20
Thanks I have them mounted, however when I try to go in the windows partition it keeps telling me that I dont have the proper permision to view the contents. Any way to change this?
tried setting unmask to 0000 and:
sudo chown -R no1enter:no1enter /home/no1enter/Desktop/windows
sudo chmod -R 755 /home/no1enter/Desktop/windows

---

### Post by noenter1 on 2007-02-20
Ok finally got it after awhile of searching. apperently it does help to have lack of sleep at times :) mounted the ntfs partition using: ```
sudo mount -t ntfs /dev/sda1 /home/no1enter/Desktop/windows -o umask=0000
```

---

