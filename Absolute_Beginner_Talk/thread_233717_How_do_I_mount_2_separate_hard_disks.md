---
title: "How do I mount 2 separate hard disks?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by joeinazyes on 2006-08-10
This is my first post and it is filled with newbie naivete.

I just installed DD 6.06 64-bit version on my system, which contains 2 80GB hard disks. Both disks are fomatted with Ext3. The OS files are fine and run well on hda. However, I don't understand why I can't use hdb normally and add folders and files as I do in MS Windows XP. I don't understand why the 2nd disk (hdb) doesn't mount on boot so that I can access it like I do /home on hda. hdb contains a blank 74.5GB partition.

I can manually mount the drive (hdb) with disk manager. However, I can't add folders and files as I would do normally with an external USB FAT32 HD. That's what I would like to do with the internal IDE slave drive (hdb) AND have that drive mount automatically on boot.

OK, here's the /etc/fstab file if it helps in some way:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by adhuvi on 2006-08-10
You might find some answers here:
[http://ubuntuforums.org/showthread.php?p=1363469#post1363469](http://ubuntuforums.org/showthread.php?p=1363469#post1363469)

---

### Post by confused57 on 2006-08-10
This link may help:

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

