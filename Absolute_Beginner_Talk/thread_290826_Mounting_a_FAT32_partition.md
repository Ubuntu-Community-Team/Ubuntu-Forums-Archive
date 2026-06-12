---
title: "Mounting a FAT32 partition"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by lorddaddy84 on 2006-11-01
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
I followed the how to at the link above and got an error.
Is this what it should look like?

---

### Post by StormNet on 2006-11-01
lorddaddy84, you have a FAT32 partition (hda1) not an NTFS, what you need in your fstab is the following line:

> /dev/hda1    /windows     vfat    umask=0000  0  0

---

