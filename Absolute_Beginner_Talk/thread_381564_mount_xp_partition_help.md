---
title: "mount xp partition help"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by dabertman on 2007-03-11
ive installed edgy eft 2 hrs new to this
im trying to follow the instructions from here: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
this is what i got with fdisk

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        3562     8128890    c  W95 FAT32 (LBA)
/dev/hda3            3563        4805     9984397+  83  Linux
/dev/hda4            4806        4863      465885    5  Extended
/dev/hda5            4806        4863      465853+  82  Linux swap / Solaris

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19929   160079661    7  HPFS/NTFS

the drive i want to mount is /dev/hdb1 .  i have the fstab file open

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=a3aa0d2a-7e93-4f9d-a3f9-56e14a2b4e2a /               ext3    defaults,erro$
# /dev/hda5
UUID=bef01933-fae1-45d9-b01b-16b235b37f56 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

how would i correctly edit this?

also would like to see all apps installed when i click on applications. like gparted so i can correct a partition size.

i feel like a baby thats just seen keys rattle in front of me. let me have those.
ill be sitting here waiting with excitement:popcorn:

---

### Post by dabertman on 2007-03-11
i cant even get this drive to do the mount thing. i get  "special device /dev/dhb1 does not exist"

is there anyone that can help me?
popcorns gone . cigs running low

---

### Post by Kateikyoushi on 2007-03-11
First let's try to mount it manually and see f it works. Copy the following lines to terminal.

```
sudo mkdir /media/hdb1
sudo mount /dev/hdb1 /media/hdb1/ -t ntfs -o nls=utf8,umask=0222
df
```

---

### Post by dabertman on 2007-03-11
first thanx for the reply.
after searching everywhere google irc etc. tried a few different things so who knows what ive done 
i found it right here: [http://ubuntuforums.org/showthread.php?p=2234056](http://ubuntuforums.org/showthread.php?p=2234056) 
very frustrated right now.:confused:  but i got it to see the drives.
again thanx

---

### Post by Kateikyoushi on 2007-03-11
Okay, then copy this to terminal.

```
ls /media
cat /etc/fstab
```

---

### Post by dabertman on 2007-03-11
parker@parker-home:~$ ls /media
cdrom  cdrom0  floppy  floppy0  hda1  hdb1  myFAT  windows
dont know why i see a second floppy as i got 2 external cdrw's
and the windows i guess i got from "sudo mkdir /windows". when trying other suggestions. 

parker@parker-home:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=a3aa0d2a-7e93-4f9d-a3f9-56e14a2b4e2a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=bef01933-fae1-45d9-b01b-16b235b37f56 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0

i can now read from the drives.

---

### Post by Kateikyoushi on 2007-03-11
Then it was already set up correctly, all you have to do is remove the myFAT and windows directories from /media because you do not use them.

---

### Post by silkstone on 2007-03-11
I'm using Edgy and that has always shown 'Floppy Drive' and 'Floppy 1' - not sure why, as there is only one floppy drive, but I just ignore it.

Re mounting other partitions.... You have to create the mount point as a subdirectory of /media. If you try to mount to any other directory you've created (e.g. /windows) the drive/partition will mount but you can't see it. It took me a while to figure this out. I've read that you can create a mount point anywhere, but that does not seem to be the case - it has to be under /media for it to be seen.

---

### Post by dabertman on 2007-03-11
i now can write to the drives.  found great instructions here: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
baby steps lol

---

