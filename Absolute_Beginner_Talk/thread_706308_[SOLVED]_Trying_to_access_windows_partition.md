---
title: "[SOLVED] Trying to access windows partition"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by boblettoj99 on 2008-02-24
Hi i recently installed kubuntu as well as windows xp (i had xp first), i went through the whole resize partition thing and both OS's boot fine. When i go to 'Storage Media' in dolphin the 2 partitions are there however i can only click on the kubuntu one. When i try to go on the windows one it says: hal-storage-fixed-mount refused uid 1000

can anyone help? ive been reading through various posts on this and i assume you need my cfdisk/fstab stuff o here goes:

```

cfdisk (util-linux-ng 2.13)

                              Disk Drive: /dev/sda
                        Size: 80026361856 bytes, 80.0 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 9729

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1                    Primary   NTFS             []              62125.54
    sda2        Boot        Primary   Linux ext3                       17100.36
    sda5                    Logical   Linux swap / Solaris               797.86


```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ecfef292-6beb-424b-8483-bc001feb4f83 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b4c0492d-73e0-48f3-b5d5-c16d943a3f84 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

please someone help :D

---

### Post by glennric on 2008-02-24
Try adding the line
```
/dev/sda1 /media/sda1   ntfs    defaults,uid=1000,gid=1000      0       0

```
to the end of the file /etc/fstab.
Then
```
sudo mkdir /media/sda1
``` to create the mount point.
Then type ```
sudo mount -a
```
You should then be able to browse /media/sda1 and see your files on the windows partition.

---

### Post by oedha on 2008-02-24
your ntfs not mounted yet......
what's the result of sudo mount /dev/sda1 /media/sda1 ?

---

### Post by boblettoj99 on 2008-02-24
thanks glennric tha did the trick :D

---

