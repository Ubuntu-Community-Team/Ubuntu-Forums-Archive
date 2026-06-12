---
title: "Automounter for FAT32 file system"
date: 2007-01-28
forum: Andhra Pradesh Team - India
---

### Post by abhiomkar on 2007-01-28
I have written a simple script to mount fat32 drives automatically. 

Download :
```
wget http://abhiomkar.googlepages.com/automounter.sh
```

Execute :
```
sudo ./automounter.sh
```

Let me know if there are any mistakes or bugs in the script

---

### Post by bharath.vegito on 2007-10-01
thank you.
u cant try a ntfs writable mount script which many people would be looking for.
best of luck.

---

### Post by bharadwaj on 2008-01-25
> **bharath.vegito said:**
> thank you.
u cant try a ntfs writable mount script which many people would be looking for.
best of luck.
Fat32 one of the disk drive format in linux besides ext2 or ext3 so it is obvious that when it fat32 linux tries to mount the partition automatically but only iwhen windows is not runing in ti I mean only when windows is properly shut down. Iam pretty sure that what ever is done by abhirom is only forcing it manually. But where is NTfs is whole new concept to linux so we need to also add the data of it for making it read and write and its not that easy. THere are many projects working on it but one is really doing a fair jo NTFS-3g it available in ubuntu by default but if you want the GUI instal it from repos

---

### Post by aiser on 2009-12-01
:popcorn:

---

### Post by abdulmajid on 2012-03-15
I thought editing only fstab file is necessary to auto mount filesystems on boot. What does mtab file do?

---

