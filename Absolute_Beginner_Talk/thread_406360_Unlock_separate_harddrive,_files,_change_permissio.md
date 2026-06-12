---
title: "Unlock separate harddrive, files, change permissions etc."
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2007-04-10
I have 2 other hard drives mounted and one contains all my mp3's. These partitions are also shared with my windows thing. I can't add any or change any mp3 files because it's locked. I tried to go in as root and changed permissions which it worked but it was still locked and said I wasn't the owner and I still don't have the ability to create files or change them. How do I own that hard drive because it's like a fake mother filtering my computer usage?

---

### Post by machoo02 on 2007-04-10
how is this drive mounted?  could you post the output of```
cat /etc/fstab
```

---

### Post by Yellowbelly on 2007-04-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd2
UUID=779576c4-aa0c-4bd4-9a60-28fe6eaf801c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=3B3D-1883  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdd1
UUID=45D7-23C6  /media/hdd1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdd3
UUID=049ec3da-9b1c-4ae9-9ace-e6e2b9e547fc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Yellowbelly on 2007-04-16
any help?

---

### Post by zvacet on 2007-04-16
Try to change owner instead of permissions.

---

### Post by Yellowbelly on 2007-04-16
how do you do that?

---

