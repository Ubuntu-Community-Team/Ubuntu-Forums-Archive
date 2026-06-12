---
title: "problem with gnome partition editor"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by newbie59 on 2007-03-13
I installed the gnome partition editor to resize my partition.
I got the following error message:
unable to read the contents of this file system. because of this some operations may be unavailable. did u install the correct plugin for this file system. 
my file system is winXPhome and I got the package on synaptic
any suggestions??

---

### Post by Kateikyoushi on 2007-03-13
The filesystem is most likely ntfs, you can be sure by using the following command.
Before you resize, run a checkdisk from windows defragment few times and backup important data.

```
sudo fdisk -l
```

---

