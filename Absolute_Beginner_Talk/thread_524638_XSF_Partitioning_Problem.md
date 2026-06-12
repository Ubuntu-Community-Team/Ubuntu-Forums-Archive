---
title: "XSF Partitioning Problem"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by V3lier on 2007-08-13
Well I just read a thread talking about how good the XSF filesystem is and I tried to switch by putting the Live CD but when I change it to XSF it tells me something like: "The GRUB boot loader installation often fails or hangs when /boot is on a XFS file system. Using LILO in this situation is recommended." I don't know how to get around it to make my filesystem XFS. I really want to use XFS because i've heard it's the fastest. Also I have another question, by using XFS will the desktop still work normally like the default filesystem? Like, can you still update properly and stuff?

---

### Post by 1/0 on 2007-08-13
Just make an 32 Mb (or so) /boot partition with ext2 and you're off with the problem. xfs is too unstable IMO for /boot.

---

### Post by bodhi.zazen on 2007-08-13
The problem is grub does not boot XFS partitions.

So you can make a /boot partitions. make it ext2

Or you can install and configure LILO : 

[http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html](http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html)

---

