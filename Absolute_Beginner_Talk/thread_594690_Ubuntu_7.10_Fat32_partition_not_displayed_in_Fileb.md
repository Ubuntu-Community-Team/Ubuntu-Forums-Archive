---
title: "Ubuntu 7.10 Fat32 partition not displayed in Filebrowser in Ubuntu but displayedin XP"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by koidenouvo on 2007-10-28
Hi,

1) I have a fat32 partition not showing along other volumes in Ubuntu File Browser. Why? How can I have it displayed as a volume?

2) I would like to have my home folder on "dossier123". It is currently located in the default home location on the file system partition.

3) I cant save a document from any application in Ubuntu on dossier123 as permission are tight. Is it ok to make this partition 777? Is it the only way to save files on this partition from a GUI application? It would very difficult with my knowledge to save let say a OpenOffice docs from the command line as sudo or gksudo ... i don't even know the difference.

Find fdisk -l and fstab ls -l output in next post.

Thanks if you can help

---

### Post by koidenouvo on 2007-10-28
root@xxx:/media# sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9bda9bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2517    20217771    7  HPFS/NTFS
/dev/sda2            2518        3490     7815622+  83  Linux
/dev/sda3            3491        3589      795217+  82  Linux swap / Solaris
/dev/sda4            3590        4864    10241437+   b  W95 FAT32

---

### Post by koidenouvo on 2007-10-28
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda2
UUID=41bdeabe-04e2-4f15-a5c6-7d3d9b144810 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda4
UUID=72AC-DCA7  /media/HomeDocs       vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda1
UUID=425C6C065C6BF359 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

# /dev/sda3
UUID=d9c54648-652c-4d21-89a1-cfe7b2a08c6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by koidenouvo on 2007-10-28
bpascal123@xxx:/media$ ls -l
total 24
lrwxrwxrwx 1 root root       6 2007-10-27 16:32 cdrom -> cdrom0
drwxr-xr-x 2 root root    4096 2007-10-27 16:32 cdrom0
drwx------ 4 root root    8192 2007-10-28 11:16 dossier123
lrwxrwxrwx 1 root root       7 2007-10-27 16:32 floppy -> floppy0
drwxr-xr-x 2 root root    4096 2007-10-27 16:32 floppy0
drwxrwx--- 1 root plugdev 8192 2007-10-27 19:16 sda1

---

### Post by BaffledMollusc on 2007-10-28
> **koidenouvo said:**
> Hi,

1) I have a fat32 partition not showing along other volumes in Ubuntu File Browser. Why? How can I have it displayed as a volume?

2) I would like to have my home folder on "dossier123". It is currently located in the default home location on the file system partition.

Find fdisk -l and fstab ls -l output in next post.

Thanks if you can help
I'm a little confused about what you're asking, but I what I think you have to do is alter the line in your fstab from this
```

UUID=72AC-DCA7 /media/HomeDocs vfat defaults,utf8,umask=007,gid=46 0 1

```
to this:
```

UUID=72AC-DCA7 /media/dossier123 vfat defaults,utf8,umask=007,gid=46 0 1

```
Your FAT32 filesystem should now show up in your file browser.

---

### Post by koidenouvo on 2007-10-29
Yes BaffledMollusc,

You've spot it right, the name of the folder in media was not matching the one in fstab. I hope this post will not make give me a Ubuntu star unless in chocolate...

By the way, are permission fine that way for this fat32 partition?

drwxrwx--- 13 root       plugdev 8192 1970-01-01 00:00 dossier123

I am not even sure fat32 has something to do with permissions. So is drwxrwx the default?

Thanks for your help and hope this reply will make more sense.

P,

---

