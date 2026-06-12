---
title: "[SOLVED] Cant write on my internal disk"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by muntaser on 2008-01-08
Please help me..... I'm using ubuntu 7.10, and I cant make changes on my vfat hard drive, because apparently I dont have permission, the only one who has permission to write or to delete files on this hard drive is root, so my quastion is how can i change the permission so user can write and delete files on this vfat hard drive.

here is my fsatb:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=219d7ec5-01af-4f9c-9e0f-a84de35d3d8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=DC7073757073556C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1
UUID=46D9-0787 /media/hdc1 vfat defaults,user 0 2
# /dev/hda3
UUID=f513a24b-5f40-daa1-7e96-6e61a7c5edbd none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


the problem is in hdc1.

Thanks for any help

---

### Post by geirha on 2008-01-08
Change the line in your fstab with one of these:
```

# This will give all users read and write access
UUID=46D9-0787 /media/hdc1 vfat defaults,users,umask=000,fmask=111 0 0
# This will give all users read access, but only administrators can write (users that are members of the admin group)
UUID=46D9-0787 /media/hdc1 vfat defaults,users,gid=admin,umask=002,fmask=113 0 0

```

---

### Post by muntaser on 2008-01-08
yea it worked, thank you vey much

---

### Post by geirha on 2008-01-08
Did you remount it? ```
sudo umount /media/hdc1
sudo mount /media/hdc1
```

What's the output of this? ```
ls -ld /media/hdc1
```

---

