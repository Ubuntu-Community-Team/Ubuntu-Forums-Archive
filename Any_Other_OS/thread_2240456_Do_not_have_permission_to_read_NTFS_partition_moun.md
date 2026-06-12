---
title: "Do not have permission to read NTFS partition mounted with fstab"
date: 2014-08-20
forum: Any Other OS
---

### Post by veddox on 2014-08-20
I recently installed Arch on my laptop as a third system, but have run into a bit of trouble with my data partition (ntfs). I mount it at startup with fstab, but as a normal user it does not even give me read access. Currently I have circumvented this by making myself part of the root group, but that seems like a bit of a security risk...

My partitions are as follows:
/dev/sda1 - Windows (NTFS)
/dev/sda2 - Data (NTFS)
/dev/sda3 - Ubuntu (ext4)
/dev/sda4 - Arch (ext4)

My fstab file:
```
# 
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
# UUID=c2fcf1ec-cd3f-4d1b-aa50-75ae8d96069d LABEL=ARCH
/dev/sda4               /             ext4          rw,relatime,data=ordered    0 1

# Mount the DATA partition
/dev/sda2    /home/daniel/Data    ntfs    rw,auto,exec,umask=007    0    0    2

# Add the swap file
/swapfile    none    swap    defaults    0    0
```

The same partition works perfectly fine on Ubuntu, here is a snippet from that fstab file:
```
# /media/DATA was on /dev/sda2 during installation
UUID=3F75BA8F22608584 /media/DATA     ntfs    defaults,umask=007,gid=46 0       0
```

What do I have to change so that normal users have read-write access to the partition?

---

### Post by Habitual on 2014-08-20
[https://wiki.archlinux.org/index.php/NTFS-3G#Linux_compatible_permissions](https://wiki.archlinux.org/index.php/NTFS-3G#Linux_compatible_permissions)

---

### Post by veddox on 2014-08-21
Thanks a lot!

---

### Post by Habitual on 2014-08-21
You are very welcome.

---

