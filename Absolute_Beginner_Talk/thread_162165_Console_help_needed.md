---
title: "Console help needed"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by Liolikas on 2006-04-18
How i can mount/unmount hdd, cd, oth in concole manualy?
How I can look which devices is accessable?
How i can mount iso files?

---

### Post by sYs^ on 2006-04-18
Mount/Unmount: ```
sudo mount /dev/hdXY /location/to/mount
sudo umount /dev/hdXY
```
It's possible you'll have to define a filesystem type like this: ```
sudo mount /dev/hdXY -t ntfs /location/to/mount
```
You can choose from these filesystems: 
```
adfs,  affs,  autofs,  coda, coherent, cramfs, devpts,
efs, ext, ext2, ext3, hfs, hpfs,  iso9660,  jfs,  minix,  msdos,
ncpfs,  nfs,  ntfs,  proc,  qnx4, ramfs, reiserfs, romfs, smbfs,
sysv, tmpfs, udf, ufs, umsdos, usbfs, vfat, xenix,  xfs,  xiafs
```
Devices: ```
sudo fdisk -l
```
Iso mount: ```
sudo modprobe loop 
sudo mount file.iso /location/to/mount -t iso9660 -o loop
```

But we have a very nice search button in the up-right corner, lol :p

---

### Post by Liolikas on 2006-04-18
Thx. 

Search did not helped me.

---

### Post by sYs^ on 2006-04-18
Ok, I edited my post before, there's some more information :> but ```
man mount
``` is helpful too

---

