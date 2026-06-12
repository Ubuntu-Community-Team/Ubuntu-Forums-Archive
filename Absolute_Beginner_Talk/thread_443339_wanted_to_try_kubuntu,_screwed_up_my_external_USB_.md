---
title: "wanted to try kubuntu, screwed up my external USB drive.. help!"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by little brad on 2007-05-14
okay, so i  wanted to try kubuntu. it wouldn't see my external USB drive, but the regular ubuntu install did it automatically. i went into the settings in kubuntu and i enabled it and got it working... but after some time with kubuntu i decided i wanted to go back to ubuntu.

now that i'm using GDM again, i can't see the drive or access it.

when i run fdisk -l, i get this

```
Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS
brad@brad-desktop:~$ 

```

what does that mean? :(

---

### Post by Austin_KW on 2007-05-14
Here you are only seeing one drive
try "sudo fdisk -l" to see all the disks

If you changed the partitions on your drive the /dev/disk/by-uuid/* may no longer match your UUIDs in /etc/fstab

---

### Post by little brad on 2007-05-14
i figured it out. somehow my NTFS config tool deselected my reading/writing of external drives. i just re-enabled it and all is well. thanks though!

---

