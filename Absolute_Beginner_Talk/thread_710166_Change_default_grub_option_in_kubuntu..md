---
title: "Change default grub option in kubuntu."
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by japc126 on 2008-02-28
How do I do it?

XP appears as the third or the fourth choice in the grub menu, if you choose to count the "other operative systems" option (yes, I started counting from zero)

---

### Post by forestpixie on 2008-02-28
edit the menu.lst so that default=xp

kdesu kate /boot/grub/menu.lst

I thiink they are the commands in kubuntu

---

### Post by uberlube on 2008-02-28
> **forestpixie said:**
> edit the menu.lst so that default=xp

kdesu kate /boot/brub/menu.lst

I thiink they are the commands in kubuntu

the correct path is /boot/grub/menu.lst

---

### Post by tangibleorange on 2008-02-28
You can also use startup manager, which uses a GUI to change GRUB manager. You can change it by installing it from Adept (in KDE) - just search for it.

---

### Post by forestpixie on 2008-02-28
:D

so it is

---

### Post by karthikbalaji on 2008-02-28
sudo vi  /boot/grub/menu.lst 

Change the value of the variable default .

It ll be like  "default         0"  ... U have to to count "other operating systems" also as one option.

If ur grub looks like,

ubuntu 
ubuntu recovery
other operating system
XP

then change "default" to 3 ..

---

