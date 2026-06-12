---
title: "Mount partition to use with disk icon on desktop"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by ImpelGD on 2007-04-25
How does one set a partition to be automatically mounted to appear as a disk in Nautilus, with its own icon on the desktop?

The Windows partition is appearing on the desktop, but the storage partition (ext3) isn't.

Thanks.

---

### Post by Happy_Man on 2007-04-25
could you please post the output of 
```
cat /etc/fstab
``` please?

---

### Post by ImpelGD on 2007-04-25
Sorry - should've included it before.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=182dc2f2-0f39-4bf4-bc54-27e21844bc4f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=59eb4c7f-3bbb-4bec-909a-d38a74d14ea1 /media/Storage        ext3    defaults        0       2
# /dev/sda7
UUID=d78722f5-a3b7-4843-828f-356dc9c98ef8 /home           ext3    defaults        0       2
# /dev/sda1
UUID=465433705433623B /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=472a2644-a355-4eed-a672-bc6acbd1aebc none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

It's sda8. I inserted '/media' myself thinking that may help, but it hasn't.

Thanks. :)

---

### Post by orb9220 on 2007-04-25
You also have then create a folder called Storage in Media folder  then reboot.

---

### Post by ImpelGD on 2007-04-25
Thanks - working now. :)

I did actually try that earlier, but neglected to name the directory with a capital S.

---

