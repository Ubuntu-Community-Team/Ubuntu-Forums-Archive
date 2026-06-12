---
title: "Change disk owner?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-05-06
roko@linux:/media/160GB$ ls -la /media
skupno 124
drwxr-xr-x  8 root root     4096 2007-05-06 17:43 .
drwxr-xr-x 21 root root     4096 2007-05-06 19:29 ..
dr-xr-xr-x  1 root root    28672 2007-05-06 17:32 160GB
dr-xr-xr-x  1 root root    65536 2007-05-06 16:00 320GB
lrwxrwxrwx  1 root root        6 2007-05-06 18:59 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2007-05-06 18:59 cdrom0
lrwxrwxrwx  1 root root        7 2007-05-06 18:59 floppy -> floppy0
drwxr-xr-x  2 root root     4096 2007-05-06 18:59 floppy0
-rw-r--r--  1 root root      150 2007-05-06 17:43 .hal-mtab
--wxr-x---  1 root root        0 2007-04-15 13:56 .hal-mtab-lock
dr-xr-x---  1 root plugdev  8192 2007-05-06 15:24 sda1
drwxr-xr-x  3 root root     4096 2007-05-06 18:59 sda3

What do I have to write in terminal to make  160GB disk owned by me?

---

### Post by taurus on 2007-05-06
What filesystem is that /media/160GB?

---

### Post by baysl on 2007-05-06
Ntfs

---

### Post by aysiu on 2007-05-06
Follow this tutorial (it includes screenshots):
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

