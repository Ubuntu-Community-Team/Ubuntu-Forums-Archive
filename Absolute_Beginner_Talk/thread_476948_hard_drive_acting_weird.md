---
title: "hard drive acting weird"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-06-17
Take a look at this:
[[IMG]http://img440.imageshack.us/img440/65/screenshot4av5.th.png[/IMG]](http://img440.imageshack.us/my.php?image=screenshot4av5.png)

When I try to access to my IDE drive which has some files I want to access I get that

---

### Post by Sonofmoog on 2007-06-17
More info needed.  What's the filesystem?  FAT32?  NTFS?  If it's FAT32 (vfat in Linux), you should have immediate access.   Linux has no problems with FAT32 partitions.  If it's NTFS, you need to be sure that ntfs-3g is installed and working properly.

---

### Post by johnnyw on 2007-06-17
> **Sonofmoog said:**
> More info needed.  What's the filesystem?  FAT32?  NTFS?  If it's FAT32 (vfat in Linux), you should have immediate access.   Linux has no problems with FAT32 partitions.  If it's NTFS, you need to be sure that ntfs-3g is installed and working properly.

yeap, its ntfs

where can I download that proggie buddy?

EDIT: found the place

---

### Post by zero244 on 2007-06-17
The easiest way to install ntfs support is download Automatix2 and install it then click on the ntfs drivers and it will mount all your partitions automatically.

---

### Post by trak87 on 2007-06-17
Are you guys sure that ntfs-3g is needed just for mounting? Ubuntu will mount ntfs natively out of the box. The only reason for ntfs-3g is for writing to ntfs partitions. Right? I've got an ntfs partition and can grab data off it all day long and I've never installed ntfs-3g.

---

### Post by johnnyw on 2007-06-18
can t find at automatix the ntfs installer :S

---

