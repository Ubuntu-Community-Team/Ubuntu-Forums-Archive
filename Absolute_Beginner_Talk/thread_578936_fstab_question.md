---
title: "fstab question"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-10-17
Yeah, why is it that the boot and swap partition are commented out, by a # ?
As in # /dev/sdb1 and # /dev/sdb5 ?  Just curious :)

  GNU nano 2.0.6                             File: /etc/fstab                                                                

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0b988614-be3a-48d4-84dc-25fe5a66e0a7 /  ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=5a9f8e1c-475d-4483-8827-d522bd4ebbd7 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda1   /media/sda1    ext3    defaults,errors=remount-ro 0       1
/dev/sda2   /media/sda2    ext3    defaults,errors=remount-ro 0       1

---

### Post by llamakc on 2007-10-17
Ubuntu now uses UUID instead of the older /dev/hdX designation.

---

### Post by Drakkor on 2007-10-17
Thanks, llamakc  , but I do think it's easer to find /dev/sb1 rather than
UUID=0b988614-be3a-48d4-84dc-25fe5a66e0a7  , lol :)

---

### Post by llamakc on 2007-10-17
> **Drakkor said:**
> Thanks, llamakc  , but I do think it's easer to find /dev/sb1 rather than
UUID=0b988614-be3a-48d4-84dc-25fe5a66e0a7  , lol :)

I do too.

---

