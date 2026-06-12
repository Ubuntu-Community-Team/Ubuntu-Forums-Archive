---
title: "Error 18 after installing Ubuntu"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by jmacsurf on 2006-12-30
ubuntu newbie here.
had an error after installing to h/d.  
GRUB Error 18

Any ideas?

---

### Post by jvc26 on 2006-12-30
Could we have a bit more data - perhaps how your disk is partitioned/computer's specs.
Error 18 occurs when basically your boot section (where the linux kernel is) is not inside the bios readable area (512MB for (E)IDE disks on older machines or larger than 8GB on others). For more info on this: [http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)
Il

---

### Post by KenSentMe on 2006-12-30
Seems like there's a problem with your BIOS handling the size of your disk. Look here: [http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

Maybe if you reinstall Ubuntu and create a small partition at the beginning of the disk for /boot the problem will be solved.

---

### Post by jmacsurf on 2006-12-30
thanks guys.  I will re-install and create a small boot partition and report results.

---

### Post by jmacsurf on 2006-12-30
During the 1st attempt I tried the option and this failed with Error 18: 
"Erase entire disk: IDE1 master (hda) - 20.0 GB  

Should I try the option:
"Resize IDE1 master, partition #1 (hda) and use freed space"

Or should I do the "manual edit partition table " option?  
If so, how much should I allocate for O/S partition?

---

### Post by Biozid on 2006-12-30
You should edit the partitions manually. Create one small partition, maybe 20mb, and set mount point /boot. Then you need one swap partion (around 1,5 times larger than your system memory) and one system partition, mount point / (root).

---

