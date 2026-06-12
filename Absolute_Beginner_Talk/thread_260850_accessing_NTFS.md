---
title: "accessing NTFS"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by woodpidgeon on 2006-09-19
I have managed to mount an NTFS partition in /mnt/windows as shown in screen shot but I still cant access the partition. It contains MP3 files.  I have tried using rhythmbox unsuccessfully.  It is probably fundermental but how do you access it?

roger@ubuntu:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/hdb3              4925556   2160348   2514996  47% /
varrun                  517920        80    517840   1% /var/run
varlock                 517920         4    517916   1% /var/lock
udev                    517920       176    517744   1% /dev
devshm                  517920         0    517920   0% /dev/shm
lrm                     517920     18856    499064   4% /lib/modules/2.6.15-27-386/volatile
/dev/hdc                713550    713550         0 100% /media/cdrom0
/dev/hdb7             20161540  10600152   9561388  53% /mnt/windows
/dev/hdb5             11928228    173084  11755144   2% /tmp/disks-conf-hdb5
/dev/hda1             20016956   6989528  13027428  35% /tmp/disks-conf-hda1
/dev/hda5             20129412  12358616   7770796  62% /tmp/disks-conf-hda5
roger@ubuntu:~$

---

### Post by shanepardue on 2006-09-19
do you have the permissions set up for access?

---

### Post by woodpidgeon on 2006-09-19
Yes, I typed sudo chmod 777 /mnt/windows in the terminal which it accepted, and in Rhythmbox I can find and open mnt and windows but the page is blank.

---

### Post by shanepardue on 2006-09-19
does your fstab allow for reading and writing? if you aren't sure how to check that type this command and paste the contents.

```
sudo gedit /etc/fstab
```

---

### Post by woodpidgeon on 2006-09-19
OK. Here it is.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb13      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb7	/media/hdb7     ntfs 	defaults	0	0

I hope this helps

---

### Post by shanepardue on 2006-09-19
so it's mounted, but you aren't able to access it? are you able to browse to the ntfs drive in nautilus (media/hdb7)?

---

