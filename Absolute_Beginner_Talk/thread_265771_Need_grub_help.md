---
title: "Need grub help"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by DoorGunner on 2006-09-26
Hi

I recently installed another linux version to test out. (embarrassingly enough)I forgot to write down my current grub.conf info for Ubuntu. 

Would someone be kind enought to copy Ubuntu grub.conf with their current kernel... (hopefully it is the same is mine)

thanks](*,)

---

### Post by bulldog on 2006-09-26
Install GRUB again and it should be fine again

Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 

Code:

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit

---

### Post by petri on 2006-09-26
You can install grub with your Ubuntu LiveCD, Here is a link for you what to do. [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by Bachstelze on 2006-09-26
If GRUB is already installed, no need to reinstall is, just let it regenerate a menu.lst :

sudo update-grub

---

### Post by DoorGunner on 2006-09-26
Ok thanks...i will give this a go

---

### Post by petri on 2006-09-26
> **HymnToLife said:**
> If GRUB is already installed, no need to reinstall is, just let it regenerate a menu.lst :

sudo update-grub


That was cool :D Thanks!

---

### Post by DoorGunner on 2006-09-26
Worked as advertised.....Thanks for the quick help

---

