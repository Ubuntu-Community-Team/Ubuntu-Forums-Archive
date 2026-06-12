---
title: "Mount not implemented?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-10-19
I'm trying to fix up my friends old Sony Vaio PCG-V505BP laptop, as Windows is corrupt on it, so I'm booting into Live Ubuntu to rescue all of her documents.

When I boot up it says that the mount function isn't implemented and that I can't access any of her hard drives.

HELP!

---

### Post by devnulljp on 2006-10-19
> **happy-and-lost said:**
> I'm trying to fix up my friends old Sony Vaio PCG-V505BP laptop, as Windows is corrupt on it, so I'm booting into Live Ubuntu to rescue all of her documents.

When I boot up it says that the mount function isn't implemented and that I can't access any of her hard drives.

HELP!

My guess is the win drives are ntfs? 
Have a look here: [http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

When you're done:
```
sudo umount /media/windows/
```

---

