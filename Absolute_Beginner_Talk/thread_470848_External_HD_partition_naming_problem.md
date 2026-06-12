---
title: "External HD partition naming problem"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by gewitty on 2007-06-11
I have an external USB hard drive on my system, which has three partitions. Ubuntu recognises it OK and names the partitions 'disk', 'disk-1' and 'disk-2'. The problem is that it seems to allocate these names randomly at each boot, so where a program such as Open Office has a files path defined in its preferences, it often throws up an error if the partition where the data is stored turns out to have been named differently in that particular session.

Is there any way to force the system to allocate the same names to the same partitions each time?

---

### Post by Najand on 2007-06-11
Make three directories in /media and then add the mount information to /etc/fstab. If you don't know how, post the output of "sudo fdisk -l" and "mount" commands.

---

### Post by pxwpxw on 2007-06-11
A clue:

with a filemanger (I have thunar in xubuntu) look in the /media directory, for hidden files (with a dot in front)
in xubuntu there is .hal-mtab,
If you read this in a text editor, it lists aliases for /dev/   names for partitions that are in use by applications.

You can separately controll what partition gets mounted where by using /etc/fstab (man fstab for info) but you need to find out how to do that.

---

### Post by noynac on 2007-06-11
I know next to nothing about renaming partitions, and I suspect   the information given in the earlier responses is the way to go. But, I recently had to rename some partitions and followed the procedures outlined in the following howto. It may be worth a look. 

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

or

[http://tinyurl.com/2sqnv6](http://tinyurl.com/2sqnv6)

---

