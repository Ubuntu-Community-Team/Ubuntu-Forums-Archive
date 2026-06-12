---
title: "USB hard drives"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-02-11
I have a 400gb external USB hard drive (western digital). I know about ntfs-3g or whatever its called, I looked at the guide on the ubuntu wiki but it look like its only for mounting them on bootup which I dont think i need. Is there a way to have read/ write access on my portable hard drive using ntfs-3g without having to mount the disc upon boot?

---

### Post by neilp85 on 2007-02-11
Add 'noauto' under options in your /etc/fstab file to the line that corresponds to your usb hdd.

---

### Post by Loki57701 on 2007-02-11
ok I opened  "/etc/fstab" and this is what I get:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=24fa298a-868d-4c8a-9f3e-c932c4999591 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=163db6f4-b5c9-46d6-b6bd-e1faaa01193a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0

-------------------------------------------------------------------------------------------------------

Im not sure which one is my USB external hard drive. If it told me the size of the hard drive I'd be good. Can you help me out here?

---

