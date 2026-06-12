---
title: "DVD recognition problem (dapper)"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by danabelle on 2007-05-04
Hi!

I've just installed Ubuntu (dapper) onto a hp pavilion a410n and have had a few problems.

The machine had a samsung DVD-ROM and a ASUS CD-RW. The ASUS is recognized, but the Samsung isn't. 

I went system-administration-disks and didn't see the asus anywhere on it.

My /etc/fstab is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Any suggestios?

---

### Post by klytu on 2007-05-05
> **danabelle said:**
> Hi!

I've just installed Ubuntu (dapper) onto a hp pavilion a410n and have had a few problems.

The machine had a samsung DVD-ROM and a ASUS CD-RW. The ASUS is recognized, but the Samsung isn't. 

I went system-administration-disks and didn't see the asus anywhere on it.

My /etc/fstab is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Any suggestios?

What is the output of ```
dmesg
```

---

