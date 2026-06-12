---
title: "Partition question"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-11-15
I had two partitions one phisycal drive I merge them with acronis in windows it is fine but in Gutsy I have one disk but I ckeck it through media I still have two icons for the two partitons (sdba/sdb5)

---

### Post by Inxsible on 2007-11-15
So did you remove Windows from the machine ?
or did you dual boot ? if you dual booted, then 1 partition is for Windows and the other is Ubuntu.

As long as they are both sd**b**, it means that its the same drive with multiple partitions on it (0-n)

---

### Post by PmDematagoda on 2007-11-15
That is because the fstab file still has the entry for the second partition, do:-
```

sudo gedit /etc/fstab
```

and do the required changes so that only the proper partition is mounted without the wrong one.

---

### Post by indytim on 2007-11-15
And delete the /media folder that is no longer in use (after youy've done the fstab cleanup).

IndyTim

---

### Post by jmfa59 on 2007-11-15
Can you explain how to do it this is what I get after running the cogec

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=80188df7-e86f-42ed-9e76-da11680445a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8A88520D8851F7E1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=38E79F8C356BDFDE /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=A037-7435  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=E1E5A19CD7F73AD7 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=10192db3-8343-44a5-aeb2-e6f1b17db550 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1   /media/sdb1   ntfs-3g   defaults,locale=en_US.utf8   0   0

---

### Post by taurus on 2007-11-15
Can you also post the output of this command from a terminal?

```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by jmfa59 on 2007-11-16
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57e4bbd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        6527    20972857+  83  Linux
/dev/sda3            6528        7833    10490445   82  Linux swap / Solaris
/dev/sda4            7834       19440    93233227+   5  Extended
/dev/sda5            7834       19440    93233196    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000971fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

---

