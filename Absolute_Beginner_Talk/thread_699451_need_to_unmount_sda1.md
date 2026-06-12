---
title: "need to unmount sda1"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by glennsbluewater on 2008-02-17
newbie here, so thanks in advance for your patiences and detailed instruction.

i have a dual boot laptop that crashed while transferring files to the xp partion of the drive.

my error reads. (and if someone can tell me how to paste this info that would help too.)

cannot mount volume

$LogFlie indicates unclean shutdown (0,0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked in use.  Choose one action: Choice 1: if you have Windows then disconnect the external devicies by clicking on the 'Safely Remove Hardware' icon in the Windows tasbar then shutdown Windows cleanly. Choice 2" if you don't have Windows then you can use the 'force' option for your own responsibility . For example type on the command line: 
 mount -t ntfs-3g /dev/sda1 /media/disk -o force [B](the response is only root can do that)
[/B]
Or add the option to the relevant row in the /etc/fstab file:   /dev/sda1 /media/disk ntfs-3g defaults, force 0 0  [B](which i was unable to do correctly)
[/B]
which currently reads: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=65c1b424-ab4c-4bde-a03b-4785c30ab5ca /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=535fd8c6-4c2f-4188-9089-7c8cf6ff5b62 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


thanks in advance for your response.

glenn

---

### Post by sb12 on 2008-02-17
> **glennsbluewater said:**
> newbie here, so thanks in advance for your patiences and detailed instruction.

i have a dual boot laptop that crashed while transferring files to the xp partion of the drive.

my error reads. (and if someone can tell me how to paste this info that would help too.)

cannot mount volume

$LogFlie indicates unclean shutdown (0,0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked in use.  Choose one action: Choice 1: if you have Windows then disconnect the external devicies by clicking on the 'Safely Remove Hardware' icon in the Windows tasbar then shutdown Windows cleanly. Choice 2" if you don't have Windows then you can use the 'force' option for your own responsibility . For example type on the command line: 
 mount -t ntfs-3g /dev/sda1 /media/disk -o force [B](the response is only root can do that)
[/B]
Or add the option to the relevant row in the /etc/fstab file:   /dev/sda1 /media/disk ntfs-3g defaults, force 0 0  [B](which i was unable to do correctly)
[/B]
which currently reads: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=65c1b424-ab4c-4bde-a03b-4785c30ab5ca /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=535fd8c6-4c2f-4188-9089-7c8cf6ff5b62 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


thanks in advance for your response.

glenn

sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force

---

### Post by glennsbluewater on 2008-02-17
fuse: failed to access mount point /media/disk: no such file or directory

---

### Post by sb12 on 2008-02-17
> **glennsbluewater said:**
> fuse: failed to access mount point /media/disk: no such file or directory

ok, first do:

sudo mkdir /media/disk

then run the original command again

---

### Post by glennsbluewater on 2008-02-17
bingo.  thank you very much for your time.

---

