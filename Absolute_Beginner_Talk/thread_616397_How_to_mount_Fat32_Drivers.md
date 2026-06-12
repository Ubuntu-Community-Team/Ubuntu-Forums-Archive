---
title: "How to mount Fat32 Drivers?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by ballot on 2007-11-18
hi i have 2 drivers c: and e: when i was using windows xp their type is fat32

that is my fdisk -l command output

root@escort:/home/escort# fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bayt
255 kafa, 63 sektör/iz, 4864 silindir
Birimler = silindir / 16065 * 512 = 8225280 bayt

   Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;  BlokSay&#305;s&#305; Kml Sistem
/dev/hda1               1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hda2            1276        4863    28820610    f  W95 Ext'd (LBA)
/dev/hda5            1276        2279     8064598+   b  W95 FAT32
/dev/hda6            3495        4863    10996461    b  W95 FAT32
/dev/hda7   *        2280        3440     9325701   83  Linux
/dev/hda8            3441        3494      433723+  82  Linux takas / Solaris

Disk bölümleme tablosu girdileri diskteki s&#305;ras&#305;nda de&#287;il
root@escort:/home/escort#


that is /etc/fstab like u see

root@escort:/home/escort# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
root@escort:/home/escort#
root@escort:/home/escort#


so what must i put to /etc/fstab
i tried somethings but i lost my drivers now i cant see in my computer section :lolflag: i rebackupped the fstab file and now will restart
thanks :)

---

### Post by anandanbu on 2007-11-18
Which version of Ubuntu have you installed ? 
If you use Gutsy both the FAT32 and NTFS drives would be mounted automatically.

---

### Post by ballot on 2007-11-18
> **anandanbu said:**
> Which version of Ubuntu have you installed ? 
If you use Gutsy both the FAT32 and NTFS drives would be mounted automatically.

i use 6.06 dapper drake

---

### Post by overdrank on 2007-11-18
> **ballot said:**
> i use 6.06 dapper drake

HI and this link may help
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
Good luck and welcome ! :popcorn:

---

### Post by ballot on 2007-11-18
but mine is fat32 he talks about ntfs :confused:

---

### Post by overdrank on 2007-11-18
> **ballot said:**
> but mine is fat32 he talks about ntfs :confused:

It does speak of fat file further down on the page. :)

Edit and please remember before making any changes to backup fstab

sudo cp /etc/fstab /etc/fstab_backup

---

### Post by ballot on 2007-11-18
thanx i solved it :guitar:

/dev/hda5 /mnt/hda5 vfat iocharset=iso8859-9,umask=000 0 0
/dev/hda6 /mnt/hda6 vfat iocharset=iso8859-9,umask=000 0 0

i did the iocharset iso8859-9 but still i cant see the turkish chars :confused:

---

