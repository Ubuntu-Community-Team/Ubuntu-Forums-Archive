---
title: "usb flash drive problem with mounting"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Rinzwind on 2007-10-23
I made a mistake.

When I was looking through properties of a mounted usb flash drive I noticed the settings under "volume" and changed the mointpoint into '/media/cruzer' but after remounting it started complaining about having a / in the mountpoint. 

Exact notice:

Unable to mount the volume. Details:
mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR (usually /).

1. how do I change this without mouting?
2. can this be considered a bug? (shouldn't the mount point be checked for validity before commiting it?)

(1) it's not in fstab:

$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e6d6f4f9-a7cb-4f15-8d0b-e7578768b3e5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=9729a6aa-427b-41f2-8e5c-69cca95f4102 /files          ext3    defaults        0       2
# /dev/sda3
UUID=8a822c0d-04c9-4feb-b198-9c54e9d7b3f1 /home           ext3    defaults        0       2
# /dev/sda2
UUID=c58cc568-d0ec-40e1-8185-08828dc73f3b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by marn on 2007-10-28
Yes, I made the same mistake!

Found the answer here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668)

You can change the key by launching the editor:

```
gconf-editor
```

select the key under "system/storage/volumes/_org_freedesktop_Hal_devices_voume_uuid_*/mount_point". Right click on key and select "edit key". In your case remove "/media/" and it should work

marn

---

