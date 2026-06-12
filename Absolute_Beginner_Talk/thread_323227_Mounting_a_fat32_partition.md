---
title: "Mounting a fat32 partition"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2006-12-21
Is there any way I can mount my fat32 partition in Edgy without any additional packages?  The partition is /dev/hda1 and the mount point is going to be /media/fatpart, so if someone could just give me the line to paste into fstab that would be great.

---

### Post by mand0 on 2006-12-21
```
/dev/hda1    /media/fatpart vfat  iocharset=utf8,umask=000  0    0
```

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

