---
title: "hdc1 error"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by KGH on 2007-05-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=20ec55ec-c0ee-414e-865d-235f50a82c3e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc2
UUID=432e983f-60aa-4d4e-b629-356dd42b152e /media/hdc2     ext3    defaults        0       2
# /dev/sda1
UUID=AC1CCB031CCAC812 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc5
UUID=378790d8-3a90-45e7-8554-b84b4eacb7ce none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I can't access hdc1 is this the problem?
# /dev/hdc1
UUID=20ec55ec-c0ee-414e-865d-235f50a82c3e /               ext3    defaults,errors=remount-ro 0       1

---

### Post by justleen on 2007-05-08
What exaclty is the problem, when you say you cant access it?
HDC1 is your mounted on your root, the /, dir. so if you cant access it, you cant boot, really..

---

### Post by candtalan on 2007-05-08
hdc1 is mounted at the root level   (  /  ) so it looks as if you are actually running the system from it. presumably the systetm is running ok(?)

Is it a question of viewing 'hidden' files I wonder?
or about 'permissions' (properties)?

---

### Post by KGH on 2007-05-08
It was a newbie mistake on my part. Thanks for the help.

---

