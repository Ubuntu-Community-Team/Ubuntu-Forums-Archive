---
title: "no joy in mounting ntfs hdd"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by novellandry on 2007-03-08
ok here is the setup

Disk /dev/hde: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        2341    18804051   83  Linux
/dev/hde2            2342        2432      730957+   5  Extended
/dev/hde5            2342        2432      730926   82  Linux swap / Solaris

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7   HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
15 heads, 63 sectors/track, 330774 cylinders
Units = cylinders of 945 * 512 = 483840 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      330769   156288321    7  HPFS/NTFS


this is what i get when i try to mount using
sudo mount /dev/hda1/media/hda/ -o ntfs -r umask=0222

any ideas on what has to be done now
i have updated fstab but still no joy

---

### Post by mahiyar on 2007-03-08
dont u think there should be space between "/dev/hda1" and "/media/hda/", another thing is, have you created directory by the name "hda" in "media"?

---

### Post by novellandry on 2007-03-08
ok i still can not access the hdd. what am i doing wrong? it says that i do not have the permissions to access the folder.

---

### Post by girishv on 2007-03-08
Did you try to access the ntfs drive as root.
sudo ls /media/hda

The ntfs driver by default do not allow writing to the ntfs partition. You have to use ntfs-3g to write.
Secondly, you can mount it such that the ntfs filesystem will be accessible to user(s). I do it by adding the 
following line to /etc/fstab

/dev/sda1 /windows        ntfs-3g    users,auto,rw  0    0

Assuming that the ntfs is in /dev/sda1 and you have created a directory by name /windows

Hope this helps

Girish

---

