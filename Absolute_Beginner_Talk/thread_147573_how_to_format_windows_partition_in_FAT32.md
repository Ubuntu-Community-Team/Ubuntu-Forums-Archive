---
title: "how to format windows partition in FAT32"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-03-20
i have winxp(installed in NTFS) and ubuntu
and another partition(32 GB) which i want to use for both xp and ubuntu
but whenever i try to format it in xp it doesnt shows FAT32 option for that partition 
can nebdy help???

---

### Post by Princey on 2006-03-20
[QUOTE=wolfmaniac]i have winxp(installed in NTFS) and ubuntu
and another partition(32 GB) which i want to use for both xp and ubuntu
but whenever i try to format it in xp it doesnt shows FAT32 option for that partition 
can nebdy help???[/QUOTE]

If my memory serves me well, WinXP by design is set to recognize FAT32 partitions >32GB but not format them. While theoretically a FAT32 partition can be up to 8 tb (terabytes) under WinXP, it won't format that size for you. One solution is to use a 3rd party partition manager or even FDISK or you can use qparted that comes with Ubuntu to format that partition. Good luck.

---

### Post by wolfmaniac on 2006-03-20
please give more details --how to use qparted

---

### Post by derelict on 2006-03-20
Why don't you format it from Linux? If the partition is, for example, hda6, you can use mkfs: ```
mkfs.vfat -F 32 /dev/hda6
```
Make sure you're formatting the correct partition, I only gave hda6 as an example.

---

### Post by Princey on 2006-03-20
[QUOTE=wolfmaniac]please give more details --how to use qparted[/QUOTE]

There are two easy ways to do it. One is using the live cd and going to your system, administration menu and chosing qparted. I've never done it from within linux as derelict suggested. If you go his way, make sure you're formating the right drive. I'm not under linux right now to give you the exact command to list your hard drives from the terminal, but I'm sure someone will give it to you before I get to boot into linux on my other machine.

---

