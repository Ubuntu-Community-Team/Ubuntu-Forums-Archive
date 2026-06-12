---
title: "access kboot.conf from liveCD (PS3)?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by neodarksaver on 2007-05-06
When i was trying to adjust the screen resolution for my ubuntu feisty on PS3, I Think i might have mistyped and messed up the kboot.cong at /etc/kboot.conf .

Now I can no longer boot into ubuntu on my harddrive.

 Is there any way I can fix this file with the Live CD? 



Thanks in advance.

---

### Post by eltorodeoro on 2007-05-08
should be able to.  if unable to access the filesystem straight away, try this:

find the partition of the HDD you need to access:
```
sudo fdisk -l
```
create a temporary mounting point for the livecd and mount that partition to it:
```
sudo mkdir /mnt/ps3
sudo mount -t ext3 /dev/hda3  /mnt/ps3
```
where /dev/hda3 matches the partition derived from the fdisk readout

from here, you should be able to edit the file you need.  these steps are from a similar but unrelated topic linked below.  a glance there may clear up some confusion, or may cause more.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

good luck!

---

