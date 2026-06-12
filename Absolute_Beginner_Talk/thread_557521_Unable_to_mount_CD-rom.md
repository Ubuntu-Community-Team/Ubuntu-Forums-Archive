---
title: "Unable to mount CD-rom"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Fixel on 2007-09-22
Hi, when I insert a cd/dvd hoping that it will automatically mount it doesn't.

I just installed a fresh version of feisty and I ran all the updates then I was going to install my nVidia 8600 card. But it needs me to insert my CD.

When inserting the CD the drive doesn't show up, except in "Computer" here it shows up but I can't browse it since:

"can't mount volume

mount: special device /dev/hda does not exist"



What should I do? (My computer is an [HP-DV9575eo](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01107337&lc=en&cc=us&dlc=en&product=3467387&lang=en))

---

### Post by Fixel on 2007-09-22
My /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=fadd04a6-42f5-4215-a8d3-241d295bc9c3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=70EFDFD70519FA89 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=4082EC3482EC2FD8 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=27ef021e-606c-45b3-9e8d-ed795db9bc37 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Pumalite on 2007-09-22
Set your CD drive to 2nd Master and 'Auto' in BIOS

---

### Post by Fixel on 2007-09-22
Will this affect my xp/vista partitions?

---

### Post by Fixel on 2007-09-22
Ok, I've got a Quanta 30CB motherboard.. it won't let me change the cd drive (it doesn't even have the option!)... what should I do?

---

