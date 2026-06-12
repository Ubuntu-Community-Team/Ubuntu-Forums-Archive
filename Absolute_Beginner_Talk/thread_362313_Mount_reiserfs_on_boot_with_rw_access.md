---
title: "Mount reiserfs on boot with rw access"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by kelbizzle on 2007-02-15
My issue is..... After I mount fstab "sudo mount -a" The partition on the second hard drive mounts fine. The problem is my user doesn't have write permissions to the drive. I check the properties of the mount point and it says it belongs to root. Here is my /etc/fstab. It that last line the correct way of mounting this type of partition?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=3aabf438-ecb2-4516-bfa5-47277c5fb267 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=97d2d1b1-6c30-4723-a9a7-3f020a6e434e none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 /media/xxtra reiserfs defaults 0 1

```

---

### Post by thenetduck on 2007-02-16
I would think that both would be 0. 
/dev/hdb1 /media/xxtra reiserfs defaults 0 0

If that doesn't work. Just do a chmod. Here is a very good guide that will help you mount a drive correctly. 
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Hope that helps, 
 The Net Duck

---

### Post by kelbizzle on 2007-02-16
yep that was it. I check it out. seems I did almost everything right up to the second zero. and the chmod. thanks alot.

---

