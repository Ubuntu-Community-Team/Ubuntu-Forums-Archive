---
title: "Uninstall Help Urgent!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Noobuntu61 on 2007-08-29
hey guys i need to clear ubuntu from my system so that i can reinstall it with a larger hard drive partiton. I dual boot with windows vista that came preinstalled on my laptop. How can i completely remove ubuntu in or to successfully reinstall it for a dual boot without losing vista?

Thanks for all your guys support!

---

### Post by Tyke91 on 2007-08-29
download the Gparted live cd, defrag and shrink your windows partition, then grow ubuntu into the available space :D

no uninstall required


EDIT: if you really wanted to completely remove something once and for all, reformat the hard drive with gparted, and then run an app called "shredder" on it.

---

### Post by maybeway36 on 2007-08-29
1. boot from a FreeDOS or MS-DOS boot disk (Knoppix should work, type [FONT="Courier New"]dos[/FONT] at the boot screen)
2. type:
```
fdisk /mbr
```
3. use a partiton editor (Knoppix comes with both GParted and QtParted) to erase the Ubuntu partitions.
You're done!

---

### Post by Noobuntu61 on 2007-08-29
that boot form a free dos should work but how do i accoplish this. I am afraid i am not as computer literate as you are my friend.

---

### Post by por100pre1 on 2007-08-29
> **Tyke91 said:**
> download the Gparted live cd, defrag and shrink your windows partition, then grow ubuntu into the available space :D

The best bet with Windows Vista is to use Vista's Disk Manager to shrink Vista's Partition (it may require some disk defragmenting, disk cleanup and removing all except last restore point in Windows) and then to use Gparted LiveCD for the Ubuntu Partitions. :)

---

