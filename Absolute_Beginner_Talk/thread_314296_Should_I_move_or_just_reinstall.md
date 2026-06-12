---
title: "Should I move or just reinstall?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-12-07
Currently I have a dual boot machine, with two harddrives.

One drive 19.01 gib contains Ubuntu 
Contains all the partition and grub loader
Partition List
Part 1 /dev/hda1  9.51 gib extended 3 
Part 2 /dev/hda2  9.09 gib extended 3
Part Swap   431mb

Two drive 40 gib contains WinXp.

C: main 9.7 gib WinXp
D: storage 13.7 gib
E: Storage 13.7 gib

What I would like to do is move the Ubuntu and all the partition to the second hard drive (40 gib) and occupy the present D: partition instead. Once this is done I will remove the 19.01 gib drive. Then move the 40 gib from secondary to primary position.

Can I easily move it or would it better to bite the bullet and reinstall Ubuntu on the D: partition?

---

### Post by bodhi.zazen on 2006-12-07
It depends on how much customization/installation you have done.

If you have a fresh install of Ubuntu it will be easier to re-install.

If you have done a fair amount of customization it will be easier to move and resize. Of course be sure to back up your data....

gparted will move and resize for you. Be sure to install grub into the MBR of the new HD.

---

### Post by aysiu on 2006-12-07
You can move it--just remember to change the /etc/fstab and /boot/grub/menu.lst files.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) should help.

---

