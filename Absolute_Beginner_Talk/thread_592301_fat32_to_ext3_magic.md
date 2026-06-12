---
title: "fat32 to ext3 magic"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-10-26
I formatted a volume (sdb1) to ext3 from fat32.   The problem is that the volume size has become a lot smaller under the new file system.  It shows in gparted as 69.12 (from the live CD) but only as 43.08 with Nautilus.

I had a look at fstab and found that the volume was still described as vfat and so I changed that to ext3.  The system will not load the desktop with that changed, there is a message that there are inconsistencies and the cli appears.

I changed this and changed the parameters and so the system will now start but the volume does not show up in any applications and still is the wrong size.   How do I fix this?


```

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/hda3

UUID=cefa2a5a-3ed7-4af9-801a-6fafaf2a21ef /               ext3    defaults,errors=remount-ro 0       1

# /dev/hda1

UUID=4633-70ED  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda1

UUID=b2160c1c-39f3-4e6d-8558-2d812637ffa8 /media/sda1     ext3    defaults        0       2

# /dev/sda5

UUID=89ab345e-e81f-420b-99a4-1f8425aac7d4 /media/sda5     ext3    defaults        0       2

# /dev/sda6

UUID=8BED-3CDA  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda7

UUID=45F7-E48F  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sdb1

# UUID=45F6-9E39  /media/sdb1   vfat    defaults,utf8,umask=007,gid=46 0       1

/media/sdb1     ext3    defaults        0       2

# /dev/sdb5

UUID=ec66d5a7-4707-4956-8488-df4396240ee7 /media/sdb5     ext3    defaults        0       2

# /dev/hda2

UUID=10d58452-8e78-4087-8507-cbd959cd760d none            swap    sw              0       0

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



```

---

### Post by taurus on 2007-10-26
The reason that /dev/sdb1 doesn't load because you never include /dev/sdb1 but a mount point only.  You need to edit /etc/fstab and make it look like this.

```
**/dev/sdb1**   /media/sdb1     ext3    defaults        0       2
```

---

### Post by expatCM on 2007-10-26
Well I can really say that I am impressed :)

Yes, spot on ....   did that and it worked exactly as needed.

Thank you for your help :)

My learning curve will continue ...................

---

