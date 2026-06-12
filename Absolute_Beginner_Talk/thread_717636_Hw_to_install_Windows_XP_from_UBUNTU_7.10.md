---
title: "Hw to install Windows XP from UBUNTU 7.10"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by raghothams on 2008-03-07
Can any one help me to install Windows XP from Ubuntu 7.10?
I'm a begginer...Pl its urgent!!!

---

### Post by Oldsoldier2003 on 2008-03-07
> **raghothams said:**
> Can any one help me to install Windows XP from Ubuntu 7.10?
I'm a begginer...Pl its urgent!!!
usually you get best results on a dual boot system if you install windows on the first partition.
then Ubuntu on the second partition.

---

### Post by wpshooter on 2008-03-07
You should install XP on your computer first and then Ubuntu, if you are really serious about this !!!

---

### Post by jken146 on 2008-03-07
You don't install Windows *from* Ubuntu, you install it from a Windows installation CD.  You'll need some free hard disk space first, though.  For that, you can use gparted -- Gnome's partition editor.  It can be installed in Synaptic or by typing ```
sudo aptitude install gparted
``` and then found in the System menu under Administration.

It *is* possible to install Windows XP after having installed Ubuntu, but GRUB, the bootloader, will get overwritten by the Windows bootloader, which won't recognise Ubuntu.  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) will help you to fix this.

---

### Post by raghothams on 2008-03-07
> **Oldsoldier2003 said:**
> usually you get best results on a dual boot system if you install windows on the first partition.
then Ubuntu on the second partition.

i've done the same...
When Windows is selected from dual boot...
The loading Windows screen comes for 2 secs and then the computer restarts.

---

### Post by BobLand on 2008-03-07
If you have a 2nd hard disk you can install Windows on that disk.  To access it, change the settings in the bios when the system boots so the boot order is determined by which disk has the operating system that you want to use.

Since you wont see any prompt, as in grub, you just have to remember to do this on boot up.  I use this type of boot up to keep my Ubuntu disk uncontaminated.

bobland

---

