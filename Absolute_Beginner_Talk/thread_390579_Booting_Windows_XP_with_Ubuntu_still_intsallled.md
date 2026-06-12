---
title: "Booting Windows XP with Ubuntu still intsallled"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Arken on 2007-03-22
How do I reinstall windows, but not uninstall ubuntu?

---

### Post by louieb on 2007-03-22
Setting up a computer to dual boot is a 3 step process.[LIST=1]
[*]Prepare partitions (GParted   live CD is a great tool for this)
[*]Install operating systems
[*]Configure boot loader (GRUB is the most commonly used boot loader)[/LIST]How to reinstall XP in you situation depends on how the computer is currently setup.
Do you have an empty primary partition large enough to  install  XP in?
If not sure boot to Ubuntu and open Applications>Terminal>Terminal and run
```
sudo fdisk -l 
```and post the output displayed here.

---

### Post by seshomaru samma on 2007-03-22
basically you will need a partition large enough to host xp
use gparted to format it as FAT32
install xp
the only problem is that xp will overwrite the MBR so when you boot the computer will only be able to access windows
no problem - you can use the LiveCD to restore Ubuntu's boot loader 
put "restore grub" in the forum's search box - you will get thousands of post explaining how , its fairly easy.

---

