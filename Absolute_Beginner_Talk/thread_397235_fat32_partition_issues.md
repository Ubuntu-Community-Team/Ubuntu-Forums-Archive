---
title: "fat32 partition issues"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Rotaj on 2007-03-30
I just installed Edgy to dual boot w/XP pro. 
The first problem is I cannot find the FAT32 partition. And once found, Can I format this shared partition from Edgy so I can store data to share between the 2 OS's?

---

### Post by taurus on 2007-03-30
You need to mount it first before you can access it.  What filesystem do you plan to reformat it to since you have use fat32/vfat to share between Ubuntu and Windows?

---

### Post by zvacet on 2007-03-30
You don´t need to format it.Leave it in fat32 and ubuntu and windows will be able to read from it.That is one of ways to share data between two OS.

---

### Post by Rotaj on 2007-03-30
I may be missing something but this is a new unformatted partition. XP wants only to format it in NTFS.

---

### Post by taurus on 2007-03-30
In that case, you can install gparted and use it to format it to vfat.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gparted
```
It will be in System -> Administration.

---

