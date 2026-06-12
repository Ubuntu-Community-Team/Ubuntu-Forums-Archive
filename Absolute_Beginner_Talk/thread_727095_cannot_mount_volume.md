---
title: "cannot mount volume"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by gavakie on 2008-03-17
I am trying to open a second drive i have in my machine when i try to go into files it tells me cannot mount volume.  do i need to just reformat the drive?  if yes how? Or what else should i do.  I though ubuntu did the formatting when I installed but I may be wrong.

---

### Post by taurus on 2008-03-17
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by gavakie on 2008-03-17
Will do when I get home thanks for the quick response

---

### Post by gavakie on 2008-03-17
Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a872a86

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9598    77095903+  83  Linux
/dev/hda2            9599       10011     3317422+   5  Extended
/dev/hda5            9599       10011     3317391   82  Linux swap / Solaris

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c9dedec

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001    7  HPFS/NTFS
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=93e64157-b4c5-4175-b508-be04800ad072 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6e526ec8-0678-482f-8943-4d5a7c69521e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              73G  3.2G   66G   5% /
varrun                268M  236K  268M   1% /var/run
varlock               268M     0  268M   0% /var/lock
udev                  268M   76K  268M   1% /dev
devshm                268M     0  268M   0% /dev/shm
lrm                   268M   34M  234M  13% /lib/modules/2.6.22-14-generic/volatile

---

### Post by taurus on 2008-03-17
So /dev/hdb1 is the one you want to mount.  See if you can mount it by hand from a terminal.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hdb1
sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1
df -h
```

---

### Post by gavakie on 2008-03-17
It worked thanks for the help.

---

