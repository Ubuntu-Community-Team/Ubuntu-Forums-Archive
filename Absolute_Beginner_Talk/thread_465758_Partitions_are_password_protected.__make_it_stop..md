---
title: "Partitions are password protected.  make it stop."
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by badrobot on 2007-06-06
after moving from edgy to feisty i found that certain hd partitions are now password protected.  i don't want them to be.  i looked into gnome-mount, gconf-editor, and the keyring manager, and i couldn't figure out how to disable this protection.  changing permissions didn't help.  any help is appreciated.

---

### Post by ambush_xx on 2007-06-06
fdisk -l

and etc/fstab

See if the mount point and device name are set correctly in fstab

see this too
[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

---

### Post by badrobot on 2007-06-06
here is the relevant output of fdisk -l:

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               2       14593   117210240    f  W95 Ext'd (LBA)
/dev/hdc5               2        5483    44034133+   7  HPFS/NTFS
/dev/hdc6            5484       14593    73176043+   b  W95 FAT32


both hdc5 and hdc6 are password protected.

and i should have said this earlier, but fstab doesn't have any information about this disk.  i'm assuming that fstab is not mounting these partitions and it's being automounted by gnome-mount.  you did give me an idea, though, that maybe if i make an entry into fstab for this disk, it will bypass the gnome-mount and will not password protect the partition.  i can try this, however, it would be nice to know how to just remove the password protection that exists with the automounting.

---

### Post by ambush_xx on 2007-06-06
back up the fstab and give it a try
it worked for me

---

### Post by badrobot on 2007-06-10
thanks ambush, editing the fstab as in earlier versions of ubuntu worked to get rid of the password protection.  although it didn't elucidate how the new automounting works, it's a fix.  thanks.

---

