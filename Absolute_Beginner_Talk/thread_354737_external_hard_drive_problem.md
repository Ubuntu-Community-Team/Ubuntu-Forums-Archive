---
title: "external hard drive problem"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-02-06
Hello.
i have an external hard drive which i use for storage and moving files about, ive plugged it in (usb 2 connection) and it is visable on the desktop, i can access the drive easily, and i can copy files from the drive, but i cant copy files to the drive or delete files from the drive, if i try to copy a file to the drive i get an error saying - you do not have permissions to write to this folder, if i try to delet a file i get an error saying - that the drive is read only.
so how can i change the permissions, i tried to change the setting by going into properties, but it wouldnt let me change things because it says its a read only drive ?
cheers.

---

### Post by taurus on 2007-02-06
Is it ntfs or fat32?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by techno-mole on 2007-02-06
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4664    37463548+  83  Linux
/dev/hdd2            4665        4865     1614532+   5  Extended
/dev/hdd5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2431    19526976    7  HPFS/NTFS

the first drive - the 80 gb is a sata drive, this is where i currently have windows.
the second drive - the 40 gb is an ide drive, this is where i have ubuntu 6.10 edgy eft.
the third drive - the 20 gb is an external drive, this is my storage drive (its actually a 20 gb laptop hard drive (my old laptop hard drive) that i put into a pocket sized enclosure)
 would it have something to do with the difference in file systems ? if so could i copy the files to the home folder, and then format the drive some how ? and how would this work when trying the drive through windows ?
cheers.

---

### Post by taurus on 2007-02-06
Sorry but you cannot write to ntfs unless you install ntfs-3g first.  As of right now, you are using ntfs driver and it is a read-only.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by techno-mole on 2007-02-06
cheers, thats worked a treat, i wanted to get it working incase i cant get the networking to, well work, with this i can move files between pc's.
thanks again.

---

