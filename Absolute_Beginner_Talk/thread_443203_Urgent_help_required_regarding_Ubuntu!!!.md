---
title: "Urgent help required regarding Ubuntu!!!"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by shashi28 on 2007-05-14
Hi,,
I am using Ubuntu 7.04 Feisty Fawn version...
I need graphical user interface for grub..
N also want to make windows xp as default selection during boot up in Ubuntu Grub...

Which command's i have to write in terminal to do all these....

N one big problem i have experienced few days back...

My Ubuntu installtion got corrupted due to which i have to install whole Ubuntu agn,,n also wixXp stops working since Grub is not loading...

Tell me ,,if i have to remove Ubuntu,,wat i have to do?
Since if i remove ubuntu,,grub also removes due to which i got error during boot up n win xp doesnt loads...

Well i am not quite familiar with linux,, just a newbie to linux...
So,,asking these type of silly questions...

---

### Post by rich.bradshaw on 2007-05-14
1) If you want to remove Ubuntu, and still have windows boot, then boot off your Windows rescie disk, go to a recovery console on this disk and type

fdisk /mbr

that will get rid of grub that get installed in your mbr.

2) To set windows as default

sudo gedit /boot/grub/menu.lst

then change default near the top to whichever number in the list Windows is. It starts with 0, so if Windows is 3rd in list, the number is 2.

---

### Post by BHelts on 2007-05-14
Now I could be wrong here, and I don't want to step on any toes, so don't hesitate to yell at me and tell me I'm stupid, but isn't the command to put into recovery console FIXMBR?

---

### Post by dpar on 2007-05-14
For a Grub GUI, see this post---------------->    [http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104)

---

