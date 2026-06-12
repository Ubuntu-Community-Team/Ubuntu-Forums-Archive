---
title: "Grub"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by TarsierSpectral on 2007-08-10
Can I edit Grub so when I am presented with the boot choices it says something else instead Windows XP Professional?

---

### Post by heimo on 2007-08-10
> **TarsierSpectral said:**
> Can I edit Grub so when I am presented with the boot choices it says something else instead Windows XP Professional?

Sure. This comes straight from my memory, so there's high chance of some mistake. But the basic thing you need to do is edit grubs configuration file. It's - if I recall correctly - /boot/grub/menu.conf. You run something like
```
gksudo gedit /boot/grub/menu.conf
```

Edit line with "Windows XP Professional", make sure not to touch anything else, not putting extra line breaks or anything like that, save, reboot to check effect. It's very important file for your system to function correctly, so be careful.

---

### Post by TarsierSpectral on 2007-08-10
when I open that file there is nothing in it

---

### Post by asmoore82 on 2007-08-10
it's '/boot/grub/menu.lst'

---

### Post by TarsierSpectral on 2007-08-10
thanks I got it working

---

