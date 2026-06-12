---
title: "Added a new hard drive"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by barbz127 on 2007-06-12
Hi all,

I have recently installed 7.04 on a new machine.

I have two hard drives, the first contains the mount point and swap partitions sda1, sda2.

Also on that drive I have a third partition in ext3 (sda3) this drive is mounted as media/sda3.

The second hard drive is sdb1 and is ext3 mounted as media/sdb1.

In the fstab I have included the below two lines:

/dev/sda3 /media/sda3 ext3 defaults 0 0
/dev/sdb1 /media/sdb1 ext3 defaults 0 0


All works for the moment until I do a kernel upgrade and I loose my drives, first I had to go through the fstab and change it to /dev/hda3 and and /dev/hdb1 and it worked, then after the next reboot I had to change it back to /dev/sda3 and /dev/sdb1.

Is this normal and how do I stop it?
Cheers,
Paul

---

### Post by southernman on 2007-06-12
I can only offer a little tidbit of info, but the kernel is actually wanting to use UUID's which they should also be in your fstab file.

If nothing else this will bring your thread back to the top for a few seconds at least. :)

---

