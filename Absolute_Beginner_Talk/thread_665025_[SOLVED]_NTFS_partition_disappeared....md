---
title: "[SOLVED] NTFS partition disappeared..."
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by caravel on 2008-01-11
This one has me scratching my head.  My /dev/hda1 is no longer mounted to /media/hda1.  I've looked at all the below places but can't seem to find why it is not there.  It was and now isn't.  Any help or pointers would be much appreciated.

```
caravel@caravel-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x079d079c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/hda5            2551        4854    18506848+   b  W95 FAT32
/dev/hda6            4855        7286    19535008+  83  Linux
/dev/hda7            7287        7529     1951866   82  Linux swap / Solaris
/dev/hda8            7530        9729    17671468+  83  Linux




caravel@caravel-desktop:~$ sudo mount -a
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hda1 /media/hda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hda1 /media/hda1 ntfs-3g defaults,force 0 0




caravel@caravel-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=2cd4fd47-f5e2-4512-92c9-fb402e3a214e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda8
UUID=c0b2f548-e488-49cf-9f29-2714f455b3a8 /home           ext3    defaults        0       2
# /dev/hda1
UUID=60E0E51CE0E4F8E4 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=D8D3-0820  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=66700d1c-d4e9-4f39-ab0f-a1191794251d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by geirha on 2008-01-11
This is a common problem with ntfs. When windows mounts an ntfs filesystem, it flags it as "in use", when it unmounts it, it removes the flag. If it wasn't cleanly unmounted (e.g. windows crashed or the power was cut or similar) you'll get that message. The best option is to boot into windows, possibly running a filesystem check just to be on the safe side, and reboot so it unmounts cleanly.

---

### Post by articpenguin on 2008-01-11
technically you dont need to run a check on ntfs as its journalled and it will roll back changes to make it into a consistant state. But yeah you should run a check if it does that.

---

### Post by caravel on 2008-01-11
That sorted it, thanks :)

---

