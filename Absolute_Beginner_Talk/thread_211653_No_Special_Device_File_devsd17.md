---
title: "No Special Device File /dev/sd*17"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by maxycatz on 2006-07-08
Trying to mount a partition on an external firewire drive.  The other four partitions mount.  In the /dev the sd* files only go up to 15.  Is this a default maximum?  How can I get partition 17 to mount?  Also, why has it moved from sda to sdb on being unplugged?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda11      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda12      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by winmac_fstab utility
/dev/sda10 /media/sda10 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/sda12 /media/sda12 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/sda13 /media/sda13 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/sda15 /media/sda15 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/sda17 /media/sda17 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/hda9 /media/hda9 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/sdb10 /media/sdb10 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/sdb12 /media/sdb12 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/sdb13 /media/sdb13 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/sdb15 /media/sdb15 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0
#Added by winmac_fstab utility
/dev/sdb17 /media/sdb17 hfsplus rw,user,file_umask=0111,dir_umask=0000 0 0



thanks

---

### Post by maxycatz on 2006-07-08
Okay, found some info on the web(dated 1999); there's a hardcoded limit of 15 partitions for scsi drives and a limit of 63 for IDE drives.  Is this affecting my setup?

---

### Post by maxycatz on 2006-07-09
Any advice or workarounds (other than repartitioning) for getting partitions above 15 to mount?

Cheers,

---

