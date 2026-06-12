---
title: "I should know this, but I am so annoyed I can't think...  FSTAB and volumes"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-05-12
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        9627    45873607+   7  HPFS/NTFS
/dev/sda3            9628        9726      795217+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9726    78124063+  83  Linux
/dev/sdb2            9727       14589    39062047+  83  Linux
/dev/sdb3           14590       19209    37110150   83  Linux
/dev/sdb4           19210       19457     1992060   82  Linux swap / Solaris
**************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5894e628-99cd-4cfa-8eef-d9f68b662d07 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=d43aa2eb-c41d-4e1e-9109-3c3d138873ba /home           ext3    defaults        0       2
# /dev/sda1
UUID=BC08D68408D63CD8 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=55626960783ED85D /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=4633-4B7C  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=e6f27024-a5ce-416c-a7ec-5aaad6c705bc /usr            ext3    defaults        0       2
# /dev/sdb4
UUID=9c2c3ac3-4047-4467-939f-67e3c422022f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
**********
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              74G  730M   69G   2% /
varrun               1013M  212K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
procbususb           1013M  140K 1013M   1% /proc/bus/usb
udev                 1013M  140K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   33M  980M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sdb3              35G  1.6G   32G   5% /home
/dev/sda1              30G   18G   13G  58% /media/sda1
/dev/sda2              44G   24G   21G  53% /media/sda2
/dev/sda3             776M   28K  776M   1% /media/sda3
/dev/sdb2              37G  2.2G   33G   7% /usr
******

I want to take SDA1's icon off the desktop, but keep it accessible in Ubuntu - BUT read only.
I want to make SDA2 READ AND WRITABLE, but take it's icon off the desktop.  
(I know it is NTFS - that's fixed in Feisty, eh?)
I want to make SDA3 stay on the desktop and be READ AND WRITABLE.  It is FAT 32 formatted. 

Please assist me in getting this done - I can't download ANYTHING from Firefox, and I need a few Windows programs.  (I am keeping XP OFFLINE now!)

THANKS!!!

MRK

---

### Post by annda on 2007-05-12
to disable automatic partitions icons on the desktop you need to run

```
gconf-editor
```

go to apps>nautilus>desktop and disable volumes_visible. you can make a manual shortcut to the partition you want to have desktop icon for.

to get an NTFS partition writable, follow this guide:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by emarkay on 2007-05-12
Thanks - between this, a crazy cat, the house chores and all that... :)

Now what about the FAT32 partition? 

BTW I did a Google search, for a few minutes last time - I will be getting back on here later and hopefully under less duress.

Thanks again!

MRK

---

