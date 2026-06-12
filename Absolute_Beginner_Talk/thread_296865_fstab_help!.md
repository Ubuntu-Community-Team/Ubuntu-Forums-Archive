---
title: "fstab help!"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by pilgrim-online on 2006-11-10
I have just altered the format on /dev/hda4 and the bottom line of the following file is wrong. [ext3 is right.]
Could someone please tell me what it should be?
Thanks

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/windows  ntfs-3g defaults,locale=en_GB.utf8   0       0
/dev/hda3       /media/ntfs     ntfs-3g defaults,locale=en_GB.utf8   0       0   
/dev/hda4       /media/ubuntu backup ext3 defaults        0       0

---

### Post by llamakc on 2006-11-10
> **pilgrim-online said:**
> I have just altered the format on /dev/hda4 and the bottom line of the following file is wrong. [ext3 is right.]
Could someone please tell me what it should be?
Thanks

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/hda4       /media/ubuntu backup ext3 defaults        0       0

Take out "backup" if you intend to mount /dev/hda4 @ /media/ubuntu

---

### Post by pilgrim-online on 2006-11-10
Thank you.

---

