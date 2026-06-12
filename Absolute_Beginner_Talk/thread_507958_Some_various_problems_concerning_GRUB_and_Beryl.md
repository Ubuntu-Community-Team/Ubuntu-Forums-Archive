---
title: "Some various problems concerning GRUB and Beryl"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-07-23
Beryl:  It keeps crashing.  I don't know why, I installed it from Synaptic.  Any help?

GRUB:  Whenever I reboot, it changes the hard drive to boot Ubuntu from to hd(1,0).  It should be hd(0,0).  How do I save it so I don't have to keep resetting it?

Thanks.

---

### Post by philter on 2007-07-23
For your Beryl issue it would be helpful if you could open a terminal and type Beryl and hit enter. It should spit out any errors that it's having and then people will be able to help more.

For Grub you can go into the terminal and execute the following:

```
 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

```

Gedit should then popup with your Grub configuration menu. Towards the bottom there is a menu entry section that should look like what you are modifying at the Grub prompt. Once you change it in there you should be good to go.

---

