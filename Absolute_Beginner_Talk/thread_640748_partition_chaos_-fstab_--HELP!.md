---
title: "partition chaos -fstab --HELP!"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by nalleballe on 2007-12-14
hi all. please help a rookie out here.. you see i have been so successful with my ubuntu lately so i deleted my entire windows partition (from ubuntu) and i got stuck with a lot of garbage after. the windows partition was hda7 and my new ext3 partition became media/disk. the thing is that in fstab hda7 is still active and in dev its still there with 19 GB of unknown data on it. the thing is also i cant seem to mount the new "disk" for all users to read and write. please guide me to get rid of the junk and to mount the new "disk" so all users can have use of it.

---

### Post by thelatinist on 2007-12-14
Any time you're asking questions about partitioning or mounting it is a good idea to post the results of

```
sudo fdisk -l <-- lower case letter l, not number 1
cat /etc/fstab
```

Chances are that's the first thing people will ask.

---

### Post by nalleballe on 2007-12-14
nat@nat-desktop:~$ sudo fdisk -l
[sudo] password for nat:

Disk /dev/hda: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x327f327e

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda2               1       19457   156288321    f  W95 Utökad (LBA)
/dev/hda5            5100        6374    10241406    b  W95 FAT32
/dev/hda6            6935        7215     2257101    6  FAT16
/dev/hda7            7216       19457    98332672   83  Linux
/dev/hda8               1        5099    40957623   83  Linux
/dev/hda9            6375        6934     4498168+  82  Linux växling / Solaris

Posterna i partitionstabellen är inte i diskordning
nat@nat-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=b5f3acdb-6a63-4b9c-ad57-5e4babefe42b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=5450-5D99  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=1C90-ECE1  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=CC584A0E5849F7AA /media/hda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda9
UUID=c2890281-c3ba-404f-9650-fc6dad417101 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


its quite stunning to see the difference... what am i doing wrong? i have used gparted to format and partion but still this..

---

### Post by thelatinist on 2007-12-14
Your fstab is trying to mount /dev/sda7 as an NTFS drive, but it is now ext3.  Do the following:

```
cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Replace the line:

**UUID=CC584A0E5849F7AA /media/hda7 ntfs defaults,umask=007,gid=46 0 1**

With:

**/dev/hda7 /media/hda7 ext3 defaults,errors=remount-ro 0 1**

Save and exit.  Restart.

---

### Post by nalleballe on 2007-12-14
thanx. now its mounted. but still the problem persists with root priviliages with the read and write. how do i get this hda7 avalible to all?

---

### Post by Phurious on 2007-12-14
```
sudo chmod +R 777 /media/hda7
```

---

### Post by thelatinist on 2007-12-14
> **nalleballe said:**
> thanx. now its mounted. but still the problem persists with root priviliages with the read and write. how do i get this hda7 avalible to all?

You could also re-edit fstab to change that line to:

/dev/hda7 /media/hda7 ext3 defaults**,umask=222**,errors=remount-ro 0 1

---

