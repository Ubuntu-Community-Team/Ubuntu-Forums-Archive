---
title: "root"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by thoeng on 2006-10-08
after downloading & installing slimserver, it functions okay but the problem is that the server does not recognize my music folder. at 1st thought the problem was unmount partition but everything work fine (find later that it is mounted)

so next suspicion is that permission problem. some guys recommend me to edit /etc/fstab file but the problem is i need to log on as root (i suppose) to edit it and i don't know how to log on as root :(

the music folder is in /hda2/music and my current fstab file is:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hda2 /media/hda2 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hda4 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by aysiu on 2006-10-08
```
sudo nano -B /etc/fstab
``` will allow you to edit the /etc/fstab as root.

More details:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

