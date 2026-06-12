---
title: "Automont new partition"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by jacktar on 2007-05-21
I deleted my Windows XP partition and created an ext3 partition. After using chown so I could wrtite on it I find it doesn't mount automatically.
I dont understand the fstab file enough to make changes to it but it looks like I could do this by right clicking on the volume --- properties --- volume --- settings.

At present it shows:

Mount Point: /media/disk
File System: ext3
Mount Options : rw nosuid nodev noexec data=ordered

Would this work ??
If so, what would I need to change it to ?

Thanks

---

### Post by justleen on 2007-05-21
in fstab you should have something like this in fstab 
```

/dev/<you devname here> /media/disk ext3 defaults 0 0 
```

---

### Post by jacktar on 2007-05-21
That didn't work. It still didn't mount after re-booting.

---

### Post by justleen on 2007-05-21
can you post the output of ```
sudo fdisk -l 
``` and the contents of your fstab?

---

### Post by jacktar on 2007-05-21
Disk /dev/hda: 20.4 GB, 20409532416 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1241     9968301    c  W95 FAT32 (LBA)
/dev/hda2            1242        2481     9960300    f  W95 Ext'd (LBA)
/dev/hda5            1242        2481     9960268+   b  W95 FAT32

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5099    40957686   83  Linux
/dev/hdb2   *        5100        9642    36491647+  83  Linux
/dev/hdb3            9643        9729      698827+   5  Extended
/dev/hdb5            9643        9729      698796   82  Linux swap / Solaris


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=075b87d6-274e-43e1-961a-2d393daa5f0a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=c27db461-01c3-429c-aa16-c3ef5ff507f0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/jim /media/disk ext3 defaults 0 0

---

### Post by drowner on 2007-05-21
> **jacktar said:**
> /dev/jim /media/disk ext3 defaults 0 0

:D

There's your problem.

You need to replace 'jim' with the correct hdax... i would presume hdb1

so

/dev/hdb1 /media/disk...etc

or, possibly

/dev/hdb1 /media/jim.......and so on, if you want to call it 'jim'

But, dont forget, you will need to create the jim directory first

sudo mkdir /media/jim/

---

### Post by jacktar on 2007-05-21
Thanks ... that did it ! ...  also solved my renaming problem.

---

### Post by justleen on 2007-05-21
look here.. Back from lunchm and yet another happy user :)

Sorry if i was to vague with my <you devname here> :)

---

### Post by jacktar on 2007-05-21
My fault .... I misread it.

---

