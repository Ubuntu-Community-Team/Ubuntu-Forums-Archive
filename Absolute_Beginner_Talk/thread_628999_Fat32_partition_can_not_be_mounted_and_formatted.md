---
title: "Fat32 partition can not be mounted and formatted"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by doowgof on 2007-12-01
I wanted to install XP and debian to a unpartitioned, blank disk. However I do not have a XP installing disk but a recovery disk, which means it only has ghost and it can not do partition and format.
Therefore I used debian to create a fat32 partition, and used guided partition option to install debian.
The installation worked smoothly (apart from it didn't recognise my internet devises), but when I booted into debian, my fat32 partition could not be recognised nor mounted. Cos I saw no formatting of the fat32 partition, therefore I guess my XP recovery disk will not work and it can not install windows, so I want to format the fat32 partition. However GParted does not allow me to format the fat32 partition to fat32. I guess this is because it is already a fat32 partition so I deleted it and created a new partition. But GParted does not allow me to create a fat32 partition! What shall I do now?:confused:

---

### Post by Nikitas350 on 2007-12-02
Try to format it to ntfs...

---

### Post by doowgof on 2007-12-02
> **Nikitas350 said:**
> Try to format it to ntfs...

I can only format it to ext3,ext2 or swap. 
Is there any command line allow me to do that?

---

