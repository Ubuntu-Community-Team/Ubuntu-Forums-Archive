---
title: "installer doesnt detect my hard drive"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by aznboi1214 on 2008-03-25
i have a custom built desktop running on a WD hard drive (250 gb), 512 ram, 2.4 pentium 4 cpu.

recently xp has been really bad so i decided to overwrite with ubuntu 7.10.  Problem is the installer goes up to partion step and cant because my hd isnt detected, i've tried rebooting and pci=nomsi(via f6 during boot command line)

i really need to get it working somebody please help me.

THanks

DN

---

### Post by c-ron on 2008-03-26
Hi,
First of all, make sure that disk isn't mounted. Bring up a terminal (Alt+F2, xterm) and issue the 'df' command. If any /dev/hd* or /dev/sd* entries show up, use the unmount command (sudo unmount /dev/hda1 for example). Other possible causes might include an incorrect setting in your BIOS. You could also try to use another partitioner like the GParted LiveCD:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by aznboi1214 on 2008-03-26
lol actually solved the problem, i had the little plastic piece on my hd indicating a dual hd computer, took it out and now it works fine, thanks though

DN

---

