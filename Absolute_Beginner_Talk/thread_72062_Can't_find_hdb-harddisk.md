---
title: "Can't find hdb-harddisk"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by gaborgraehn on 2005-10-05
Hi, 
I am running breezy preview but can't find my other (secondary slave) harddisk which I had just (before installing ubuntu) reformatted til FAT32 (to share with windows). I assume it should be called something like hdb1 but can't find anything like it in my fstab (see below).
Any ideas?
Gabor (-:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    umask=000 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by xaverx on 2005-10-05
check your bios settings, to find that disk

---

### Post by gaborgraehn on 2005-10-05
BIOS detects the harddisk and I can use it all right with Win2K (dual boot). 
Gabor (-:

---

### Post by matthewv on 2005-10-05
Your secondary slave will most likely be /dev/hdd... the partitions on that drive will then be called hdd1, hdd2, hdd3, etc...

---

### Post by gaborgraehn on 2005-10-05
Sorry but I can't figure this out.
My fstab names but one hdd and calls it cdrom (this is probably what it is).
My secondary harddisk has only one partition but doesn't appear anywhere in linux. :???:

---

### Post by SilentCacophony on 2005-10-05
Hi. if you run this in a teminal, it'll print info on your disk setup:

**sudo fdisk -l**

mine looks like so:

```
Disk /dev/hda: 20.4 GB, 20493656064 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2         312     2498107+   b  W95 FAT32
/dev/hda2             313         697     3092512+  83  Linux
/dev/hda3             698        1338     5148832+  83  Linux
/dev/hda4            1339        2491     9261472+   f  W95 Ext'd (LBA)
/dev/hda5            1339        1851     4120641   83  Linux
/dev/hda6            1852        2364     4120641   83  Linux
/dev/hda7            2365        2491     1020096   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1247    10016496    c  W95 FAT32 (LBA)
```

You should see */dev/hdb1* similar to mine. If not, post what your output was.

To mount it manually, see [http://ubuntuguide.org/#automountfat]("http://ubuntuguide.org/#automountfat"), changing the /dev/hda1 reference to /dev/hdb1 (if that is correct; see above.)

---

### Post by matthewv on 2005-10-05
[QUOTE=gaborgraehn]Sorry but I can't figure this out.
My fstab names but one hdd and calls it cdrom (this is probably what it is).
My secondary harddisk has only one partition but doesn't appear anywhere in linux. :???:[/QUOTE]

Does your cdrom work... if so, then hdd is almost certainly your cdrom...

If your drive is primary slave, it will be hdb.. just follow the instructions here to mount  it... [http://www.ubuntuguide.org/#windows]("http://www.ubuntuguide.org/#windows")

---

### Post by SilentCacophony on 2005-10-05
I should add that if after mounting it as above, gnome may not automatically add it to your *places > computer * list without logging out and back in first, but you can always navigate to the /media directory and access it from there.

---

### Post by patrick295767 on 2005-10-05
I usually first of all check the /dev/ with 
gparted 
or qtparted ... 
before mounting them. 

maybe that can help you ... 
I hope

---

### Post by gaborgraehn on 2005-10-05
Hi again,
yes, it worked. The fdisk-command listed my secondary disk all right and i mounted it as media. After a restart (not a logout/login) it was there on the desktop.
Thanks to all, now I hope to figure out my keyboard problem...
:)

---

