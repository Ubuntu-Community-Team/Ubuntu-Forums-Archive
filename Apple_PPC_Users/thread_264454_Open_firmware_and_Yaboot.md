---
title: "Open firmware and Yaboot"
date: 2006-09-24
forum: Apple PPC Users
---

### Post by refdoc on 2006-09-24
Am using my ibook 12" G4 now exclusively for over a year in Ubuntu without ever booting back into MacOSX. I am planning to delete teh MacOSx partition

Is it possible to speed up, boot, to remove yaboot and get OpenFirmware to boot directly Linux?

Which partitions do I need to keep? I presume hda2 can go?

My fdisk -l /dev/hda

> /dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled            29296875 @ 2018      ( 14.0G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                 3996094 @ 92910222  (  1.9G)  Linux swap
/dev/hda5         Apple_UNIX_SVR2 untitled            63611329 @ 29298893  ( 30.3G)  Linux native
/dev/hda6         Apple_UNIX_SVR2 untitled            15541276 @ 96906316  (  7.4G)  Linux native
/dev/hda7               Apple_HFS Apple_HFS_Untitled_9  43853880 @ 112447592 ( 20.9G)  HFS


---

### Post by didg on 2006-09-25
I don't think so, IIRC open firwmare can only boot from an hfs, iso9600 or fat fs.
 
Look at timeout and delay in yaboot.conf man page.

---

