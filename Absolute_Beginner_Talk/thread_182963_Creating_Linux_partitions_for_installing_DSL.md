---
title: "Creating Linux partitions for installing DSL"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by SDREnate on 2006-05-27
I've been using Ubuntu for about a month, so I'm a complete Linux noob. Anyway, I've been working on installing Damn Small Linux on a 300 MHz, 32 Mb RAM machine. I've been attempting to follow [ this guide](http://www.damnsmalllinux.org/talk/node/64), but when I type: ```
sudo su
cfdisk /dev/hda
``` I get this message: ```
FATAL ERROR: Cannot read disk drive
```
The drive was formatted using Windows 95 (the original operating system), so I guess that it's FAT32. Do I have to create Linux partitions?

edit- Nevermind. I figured it out.

---

### Post by mostwanted on 2006-05-27
Please post your solution!

---

### Post by SDREnate on 2006-05-27
[QUOTE=mostwanted]Please post your solution![/QUOTE]
This shows what a noob I am..I kept trying to create the partitions in hda, but hda was my cdrom drive, while hdc was my hard drive. So I created the swap on hdc1 and the DSL partitition on hdc2 and installed to hdc2, and now I'm running Damn Small Linux just fine.

---

