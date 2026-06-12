---
title: "help . . . my beleaguered fstab"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-06-26
Hello --
I am **[SIZE="3"]having [COLOR="Red"]trouble mounting hda4[/COLOR][/SIZE]** below which is a 1 GB FAT32 partition.
Please help me to edit my FSTAB document far below, so that this hda4 will
[SIZE="3"]**mount at startup**[/SIZE].
[SIZE="4"]Thanks!!!![/SIZE]


Here are the results of my fdisk -l:

```
>
>
loginname@ubuntu:~$ sudo fdisk -l


Disk /dev/hda: 20.0 GB, 20020396032 bytes
16 heads, 63 sectors/track, 38792 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       29460    14847808+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           36386       38792     1212907+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/hda3           31557       36386     2433847+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           29469       31557     1052257+   b  W95 FAT32
Partition 4 does not end on cylinder boundary.
/dev/hda5           36386       37932      779121   83  Linux
/dev/hda6           37932       38792      433723+  82  Linux swap / Solaris

Partition table entries are not in disk order

>
>

```

.
.
.
.

.


[SIZE="3"][B][I]And here is my current working FSTAB  (except for that FAT32 partition not being mounted in Ubuntu).  Everything else in this FSTAB is working fine including read/write to the NTFS partition.  I have created the appropriate 
directory "extraspace" with the mkdir command.  I've tried a few variations in my fstab
file such as /media/extraspace but it doesn't work for me, so there must be more to it.[/I][/B][/SIZE]


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=11a48ce6-cc53-45b9-85cb-0c1852485627 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=3181-1A2D  /extraspace     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=b548e55b-6793-40be-8260-dc0e015c429f /home           ext3    defaults        0       2
# /dev/hda1
UUID=94CCF5C5CCF5A222 /media/hda1     ntfs-3g    defaults,locale=en_US.utf8   0    0
# /dev/hda6
UUID=028f927e-4a16-4fba-ae99-903c6debccfb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by ugm6hr on 2007-06-26
This is helpful:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I think this is what you want to try in fstab under the # dev/hda4 line:
```
/dev/hda4 /extraspace vfat iocharset=utf8,umask=000 0 0
```

---

### Post by molly_001 on 2007-06-26
[ previously posted - removed ]

---

