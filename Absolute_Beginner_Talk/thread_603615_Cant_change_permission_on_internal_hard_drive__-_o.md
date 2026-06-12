---
title: "Cant change permission on internal hard drive  - operation not permitted"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-11-05
sdb1 is my windoze HD after a fresh install of gutsy it comes up as root and gives the following error.

sudo chown philcb /media/sdb1
[sudo] password for philcb:
chown: changing ownership of `/media/sdb1': Operation not permitted

Its owner is root. group is root but even with sudo or gksudo nautilus it wont let me change its permission

---

### Post by bswilson on 2007-11-05
If that partition is mounted, you cannot change ownership.  Unmount the internal drive then reapply your **chown** command to modify the ownership.  Also double check the filesystem table (/etc/fstab) to ensure that the **user** flag is set for the mount point.

---

