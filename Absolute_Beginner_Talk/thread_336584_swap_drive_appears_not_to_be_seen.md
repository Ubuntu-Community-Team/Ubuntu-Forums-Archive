---
title: "swap drive appears not to be ?seen"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-01-11
Using an application GKrellM I appear not to be accessing my swap partition;

fstab is ;


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=45423e02-abeb-4dd1-b410-9f2ce99cfefc /               ext3    defaults,erro$
# /dev/hda5
UUID=e0afcdbd-4e6f-465b-8774-c1b59653ddfe none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda3 /storage ext3 defaults 0 0
/dev/hda2 /data ext2 defaults 0 0
/dev/hda4 /swap linux-swap defaults 0 0

can anyone see an issue in this file?

tchoklat

---

### Post by yabbadabbadont on 2007-01-11
Never mind.

---

### Post by taurus on 2007-01-11
The entry for swap in /etc/fstab should look like this.

```
/dev/hda4   none   swap   sw   0   0
```

---

### Post by tchoklat on 2007-01-12
thanks dude

---

