---
title: "quick question about dual boot xp/ubuntu"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Steve215 on 2007-05-03
I'm new to Linux and while I wish to eventually switch to Linux altogether now now I want to dual boot XP and Linux and make XP my default OS. I've already got Windows XP Pro installed. On a seperate hard drive I'm going to install Ubuntu 7.04. From all of the dual boot tutorials I've read I'm still really confused though. If I install Linux will Grub automatically detect my XP installation and setup the dual boot correctly?

Here's my current setup:

AMD64 3400+
1GB DDR Ram
ATI X800 Pro video card
250GB Sata HDD with Windows XP professional installed
80GB IDE hdd (I'll be installing Ubuntu 7.04 onto this drive)

---

### Post by orb9220 on 2007-05-03
Yes it will see it and add it to the grub.

---

### Post by jkblacker on 2007-05-03
When you first boot you computer you'll be presented with the list of operating systems present; all you have to do is scroll down to xp and press enter. There is a time limit, though, before it defaults to ubuntu if you don't press anything, so you have to be at your computer to choose xp. I'm not sure if you can change the default with grub, but I'm sure someone else here will know.

---

### Post by Steve215 on 2007-05-03
Awesome, thanks for the help. I should have known I was making it more difficult than it really was. ](*,)

---

### Post by Nekiruhs on 2007-05-03
Yes, you can change the default. Just open the menu.lst (/boot/grub/menu.lst) and make sure the default is highest on the page.  But if you want XP default, mkae sure you put it before the Automagic kernal list. And if you want Ubuntu defualt, just put it below the Automagic Kernel List.

---

