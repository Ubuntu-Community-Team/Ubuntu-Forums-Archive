---
title: "Partition problems"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2008-04-10
I am trying to mount two primary partitions by UUID, however blkid will not give me the UUID's for those partitions.  Suggestions?

---

### Post by Calash on 2008-04-10
Going off of memory here, but I think you can get the UUID by brosing to /dev/drives/by-uuid/ and seeing what is listed there



edit:  /dev/disk/by-uuid is the correct path to look

---

### Post by Fire_Chief on 2008-04-10
You could just mount them by device name instead (/dev/hdX or /dev/sdX). Simply remove the UUID from /etc/fstab (assuming you are editing it for future mounting) and put the appropriate device and partition info.

---

### Post by dreadh3ad on 2008-04-10
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=648870e4-b3f5-4f73-bff7-b8bdf9e7bebc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3464BD0B64BCD13A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=e9a34693-ba42-4260-88e5-7ab14ea4828f none            swap    sw              0       0
# /dev/sbd3
/dev/sdb3	/media/sdb3	ext2	defaults,errors=remount-ro 0       1
# /dev/sbd4
/dev/sdb4	/media/sdb4	fat32	defaults,errors=remount-ro 0       1

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

sdb3 and sda1 are on my desktop but sdb4 is nowhere to be found.  i do not have write permissions on sdb3 despite using chmod 770 sdb3

---

### Post by bodhi.zazen on 2008-04-10
You need sudo for bklid

```
sudo blkid
```

If that fails,

```
ls -l /dev/disk/by-uuid/
```

> bodhi@VirtualUbuntu:~$ sudo blkid
[sudo] password for bodhi:
/dev/sda1: UUID="957439b4-aec7-47de-b8a5-940931956b8d" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda2: TYPE="swap" UUID="7da0c203-4ef9-491c-9215-add3ba009b7a"

bodhi@VirtualUbuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-04-06 12:41 7da0c203-4ef9-491c-9215-add3ba009b7a -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-04-06 12:41 957439b4-aec7-47de-b8a5-940931956b8d -> ../../sda1
bodhi@VirtualUbuntu:~$

---

