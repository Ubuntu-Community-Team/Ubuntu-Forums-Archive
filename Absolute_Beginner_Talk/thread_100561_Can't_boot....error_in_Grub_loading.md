---
title: "Can't boot....error in Grub loading"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2005-12-07
I attempted to boot after attempting resizing NTFS. Grub wouln't load properly. Rescue boot wasn't successful. Is there a way to restore Grub, or maybe boot directly into Linux bypassing Grub?

Below is my partition table. space between NTFS and FAT32 is not showing.

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       46729    23551258+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           67050       81409     7237282+   c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3           81409      114782    16820055   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4          114782      116280      755055    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5          114782      116280      755023+  82  Linux swap / Solaris

---

### Post by mdsmedia on 2005-12-08
OK I thought of a possible workaround (which is better than working from the Live CD anyway)

I reinstalled Hoary in the free space.

Now I need to know how to mount the old Hoary partition. I can't boot into it. I managed to boot into XP after the reinstall of ubuntu and Grub.

---

