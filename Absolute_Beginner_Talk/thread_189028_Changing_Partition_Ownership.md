---
title: "Changing Partition Ownership?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Gijith on 2006-06-04
Hello,

I'm wondering what's the best and easiest way for me to change the ownership of 3 entire paritions I have. One is NTFS and two are VFAT. I used to use kubuntu, and found this very easy, as there was a option under system settings. In gnome, I'm clueless. Here's my fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd1       /media/hdd1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thanks a bunch.

---

### Post by Mustard on 2006-06-04
Have a read over this section of a Breezy Badger guide on the subject...

[http://easylinux.info/wiki/Ubuntu#Windows](http://easylinux.info/wiki/Ubuntu#Windows)

---

### Post by aysiu on 2006-06-04
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Gijith on 2006-06-04
Thanks guys. I looked at your links and a few other places... Should something like this achieve what I want?

/dev/hdd1 /media/hdd1 vfat iocharset=utf8,uid=1000,gid=1000,umask=000  0    0
/dev/sda1 /media/sda1 ntfs nls=utf8,uid=1000,gid=1000,umask=0222 0    0
/dev/sda3 /media/sda3 vfat iocharset=utf8,uid=1000,gid=1000,umask=000  0    0

 And if so, do I just edit fstab and reboot? Thanks again.

---

### Post by Mustard on 2006-06-04
The uid=1000, gid=1000 stuff would only be necessary if you were trying to restrict access to just one user or one group.  The methods shown in the two links above would give access to all users.  I don't know whether its really worth using them in combination with the umask settings. Personally I would just be using the examples given in the two links above...

```
/dev/hdd1 /media/hdd1 vfat iocharset=utf8,umask=000 0 0
/dev/sda1 /media/sda1 ntfs nls=utf8,umask=0222 0 0
/dev/sda3 /media/sda3 vfat iocharset=utf8,umask=000 0 0

```

You would edit the /etc/fstab file, then **umount** those specific devices, then **sudo mount -a** , which would mount all entries in the fstab file.

---

