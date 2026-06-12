---
title: "Mount win fat32 partiton to be writable"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by ltk5 on 2007-04-17
I'm trying to mount a windows fat32 partition, so it can be both readable and writable. At the moment, when I mount it (sudo mount  /dev/sda1). The owner is root. How to change this, or can I set the mount options for all users?

Thanks!

---

### Post by Bekker on 2007-04-17
This might help you: [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

In short: the file /etc/fstab holds the information on how to mount certain devices. To make some device writable make sure "rw" or "defaults" is in the options.

---

### Post by orb9220 on 2007-04-17
Mine for fiesty is:

> /dev/sdb1     /home/orb/Drives/114GB-fat32/     vfat    defaults,utf8,umask=007,gid=46 0       0

---

### Post by Jagot on 2007-04-17
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html)

---

### Post by ltk5 on 2007-04-17
the problem is i don't want to make in auto-  available... 
but, ok, now i will

---

### Post by Jagot on 2007-04-17
As you're using Edgy, at the end of your fstab file append the line:

```
/dev/hda1 /media/windows vfat umask=0000
```

This assumes you have a /media/windows directory to mount it to.  Adjust as necessary.

---

### Post by ltk5 on 2007-04-17
thank you! 
now i can write to my win partition :D

---

