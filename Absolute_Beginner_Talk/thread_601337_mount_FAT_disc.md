---
title: "mount FAT disc"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by nalleballe on 2007-11-03
hi! im having trouble (under KDE) to mount a FAT disc forever (and not just during the current session)

the disc is located at mnt/hda5

in fstab:

/dev/hda5       /mnt/hda5       vfat    noauto,users,exec,umask=000     0      0

please help.

---

### Post by ofb on 2007-11-03
You've got it set for 'noauto'.

Two good references,
In terminal, enter: man mount
[http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)#noauto:_don.27t_mount_at_boot](http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)#noauto:_don.27t_mount_at_boot)

---

