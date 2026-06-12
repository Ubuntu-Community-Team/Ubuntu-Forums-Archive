---
title: "hang on partition check"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by twist2b on 2007-12-22
sorry but i cant load ubuntu anymore and im dieing.... it starts checking the partition every 30 times it seems... but on checkup it ALWAYS freezes... anyway to bypass this?

i thought i could go into recovery mode and not have to deal with it.... but thats not the case seeing that i have to checkup on recovery mode aswell aparently... once i can get in ill just do this..

[PHP]Sudo tune2fs –c 0 /dev/sd1[/PHP]

any way to bypass though?

---

### Post by ctyc on 2007-12-22
From /etc/fstab man page:

The  sixth field, (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are
       done at reboot time.  The root filesystem should be specified with a fs_passno of 1, and other  filesystems  should
       have  a  fs_passno  of  2.   Filesystems  within a drive will be checked sequentially, but filesystems on different
       drives will be checked at the same time to utilize parallelism available in the hardware.  If the  sixth  field  is
       not  present  or  zero,  a  value  of zero is returned and fsck will assume that the filesystem does not need to be
       checked.

---

