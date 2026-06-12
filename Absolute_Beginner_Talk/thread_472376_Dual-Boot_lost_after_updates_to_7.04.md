---
title: "Dual-Boot lost after updates to 7.04"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Gofer on 2007-06-13
Hi,  I'm new to Linux so please be patient

I loaded 7.04 in a 50Gb partition on my 250GB data drive and dual boot into XP Pro.
I installed the updates that were presented upon startup, everything good. Dual boot works just fine.
Messed around with customized look and feel - OSX theme - everything still good.
Installed second set of updates, Menu.lst gets changed each time ubuntu loads and dual boot section is gone, I have to manually edit the file each time but the system will not create a backup of the file.
Did I do something wrong? Can someone help?  This loss of dual boot is quite annoying.

Thanks
Gofer

---

### Post by tchoklat on 2007-06-13
open a terminal and enter
 
sudo /menu/boot/menu.lst
 
check that you have the correct entry for Ubuntu (with the correct kenel and the correct drive/partition number) and an entry for XP
 
Amend if necessary
 
Ctr X
Y
enter
 
 
to save and exit

---

