---
title: "[SOLVED] how to change an EXT3  UUID  with a live distro?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by rmx on 2008-01-14
Hello,

With Acronis I made a backup of my ubuntu partition.
With Acronis I restored this partition.

the problem is: I had to erase the partition in order to Acronis copy the backup to unallocated space.
so the UUID changed and now it seems that I have one of two options (Reinstalation is out of chance):
1. change all the files that uses UUID ( I've changed the fstab and /boot/grub/menu.lst. but this didn't work)
2. change the UUID to the old value.

Since 1st did fail (I don't have idea which more files I need to change the UUID) I'm trying the 2nd one.

With ubunto live CD I tried tune2fs but the output was invalid filesystem.
Maybe because the filesystem is EXT3 and not EXT2.
So, maybe it would work with tune3fs, but live CD 7.10 doesn't have it.

With live CD I can't access the net (wireless)

how can I solve this problem?

thank you

rmx

---

### Post by logos34 on 2008-01-14
Save yourself the trouble and take out the UUID's for that partition in menu.lst and fstab.

In menu.lst replace

root=UUID=xxxxx-xxxx....

with

root=/dev/sda1 (or whatever your partition is)

Replace the UUID in fstab with '/dev/sda1' format

---

### Post by rmx on 2008-01-14
It worked out!!!

thank you very much logos34

---

### Post by logos34 on 2008-01-14
you're welcome.  enjoy

---

