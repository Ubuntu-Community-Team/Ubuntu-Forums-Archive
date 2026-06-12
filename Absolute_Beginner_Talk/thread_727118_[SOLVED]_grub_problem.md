---
title: "[SOLVED] grub problem"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Samrat Rao on 2008-03-17
i have ubuntu 7.10 and windows xp in my PC. i reformatted a partition from windows and made two logical drives. then from ubuntu using gparted software from the repositories, i formatted one of the new partitions to ext3 filesystem. i was not properly aware of the mounting procedure using /etc/fstab and i guess i put the root options to this new partition as well. to undo this i reformatted the two new partitions again from windows and viola! the grubloader vanished and no OS will boot. what do i do?

---

### Post by Nythain on 2008-03-17
re-install ubuntu, and at the end, grub will re-install, and all should be fine...
or
look into a grub boot disk to fix/re-install grub back into the mbr... first one that showed up on a google search [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by gorgon on 2008-03-17
you need to install grub again, or maybe just make a new menu.lst file.. if that sounds confusing you should try the Super Grub Disk. Although I havent tried it it sounds nice and easy, a bit like gparted.

good luck and tell us how it goes!

Edit: @ Nythain, got me by a minute there :)

---

### Post by sandysandy on 2008-03-17
boot into live ubuntu Cd and post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR] (in terminal)


for grub re-install have a look at the thread

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

