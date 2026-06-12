---
title: "GRUB issues"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Bostonian on 2007-07-04
EDIT: problem resolved. I got frustated at this for hours and the moment i posted i managed to get it working :oops:

I recently installed XP pro on my computer, and now its boots straight to XP. after reading the forums, especially [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) i decided to try to to reinstall grub. I'm getting ```
grub> setup (hd   *(tab)*
 Possible disks are:  hd0 hd1

grub> setup (hd1, *(tab)*
 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 2,  Filesystem type unknown, partition type 0x7

grub> setup (hd1,0)

Error 12: Invalid device requested

grub>

```

can someone explain or refer me to a guide for setting up a dual boot?

---

### Post by Vajra Vrtti on 2007-07-04
Enter the commands exactly as described in that thread and it will work.

---

### Post by alienexplorers on 2007-07-04
Enter live-CD and boot it.
Enter terminal and type sudo grub
Enter:
> find /boot/grub/stage1
you will get an output like (hd#,#)
Enter:
> root (hd#,#)
setup (hd#)
in the setup line leave off the partition number.  Just use the disk number.
quit grub
reboot

---

