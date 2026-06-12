---
title: "Why does it take so long to open floppy?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-07-16
Why does it take so long to open floppy?
I am using gedit to edit files, some of the files are on floppy.
When I have started and choose,
File
Open
Double click Floppy

It takes about 2 minute for it to open.
It sounds like it searching the disk for that amount time.

Is there a shorter why of mounting the floppy?

---

### Post by %hMa@?b&lt;C on 2006-07-16
post your /etc/fstab file you can view it by typeing 
"gedit /etc/fstab" in the terminal

---

### Post by gargoyle on 2006-07-16
I am in the process of moditfing it as to mount all of my partition which I have in Winxp.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb6 /fat_files vfat iocharset=utf8,umask=000 0 0


So if you suggest any chances I can incorporate them when I edit it again.

---

### Post by catlett on 2006-07-16
One issue may be that you don't have a floppy entry in your /etc/fstab .
Put this line in and see if it helps with the mouinting.
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
This is a good short synopsis of /etc/fstab you might want to check out since your editing.
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Sef on 2006-07-16
> /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

What I did to get mine working was change auto to **vfat**.

Here's a previous post:

[Floppy]("http://ubuntuforums.org/showthread.php?t=194945&highlight=Floppy")

---

