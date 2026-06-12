---
title: "GRUB bootloader + Windows"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-01-06
I have removed ubuntu from my laptop and I have XP set on it, but no bootloader. Is there some sort of "linux" that is just a bootloader, like GRUB, that i can install? (i don't have an XP recovery disc, so I can't use an XP bootloader)

---

### Post by kbsuperstar on 2007-01-06
I was wondering, too, if Ubuntu and GRUB are actually put on separate partitions? If so, is it possible for me to simply delete the partition with Ubuntu while still using GRUB?

---

### Post by ajmorris on 2007-01-06
no. grub is installed on the same partition, (/boot/grub). 
It might be possible, however, if you have i grub disk to install grub by itself onto a partition to boot of it.

---

### Post by kbsuperstar on 2007-01-06
Anyway to get an .iso of a grub bootloader?

---

### Post by ajmorris on 2007-01-06
it's not and iso. Get the grub install and put it on a floppy.

---

### Post by rccharles on 2007-01-07
Would it be possible to create a small partition and put grub on it?

I guess you could delelete most of the files on the partition and compress the partition leaving grub on the partition.  


I have not done either.

Robert

---

### Post by CroEragon on 2007-01-07
> **kbsuperstar said:**
> Anyway to get an .iso of a grub bootloader?

There is .iso called SuperGRUB. If you have only windows i dont see reason to install GRUB, you can use Windows default bootloader. Just go into recovery console and type fixmbr. Easyer way would be downloading SuperGRUB and burning it on CD and thern just using option that does same as fixmbr. Buts default Windows bootloader on MBR.
Download it from [here.]("http://forjamari.linex.org/frs/download.php/458/sgd_0.9534_EN.iso")

---

