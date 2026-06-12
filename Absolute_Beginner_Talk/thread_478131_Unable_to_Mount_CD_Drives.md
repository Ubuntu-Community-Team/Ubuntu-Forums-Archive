---
title: "Unable to Mount CD Drives"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by aludlum on 2007-06-19
I am very new to ubuntu.  I have installed the OS, but I can not get it to recognize my 2 cd rom drives.

One CD Rom give this error message: mount: special device /dev/hdc does not exist

The other gives this: mount: special device /dev/hdd does not exist

Thanks for any help, I'm certainly finding this all confusing.

---

### Post by Ozeuss on 2007-06-19
look into this thread: [http://ubuntuforums.org/showthread.php?t=24886]("http://ubuntuforums.org/showthread.php?t=24886")
and also post your fstab file (/etc/fstab).
it might be even quicker for you to find more threads about this issue.

---

### Post by aludlum on 2007-06-20
I tried the thread and just couldn't seem to get anything to work.  I did get this information:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=6f641667-5fdf-4ef6-997c-b6d21fba0e7a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda3
UUID=29a550ad-24c6-46f0-8323-fd332700b72e /media/hda3 ext3 defaults 0 2
# /dev/hda5
UUID=af76221a-1efb-4831-87b4-1540ede4ea23 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

I don't know if that gives you any clues.  I'm worried this stuff is beyond my abilities.

---

