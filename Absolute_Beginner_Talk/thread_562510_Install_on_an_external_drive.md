---
title: "Install on an external drive"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by pcostanza on 2007-09-28
I already have a dual boot (XP/Vista) and have an external SATA drive (esata cable connection) that I would like to install Ubuntu on.  However, I don't want to have it part of the boot sequence....I want to be able to boot directly from the external drive.  What's the best way to do this and not have grub on the  XP/Vista system at all?  Any guides I can follow?
I have Ubuntu on a dual boot of another system with Vista but I'm not very experienced with Ubuntu yet so I want to be sure I do this right.
This is a great forum with many helpful people.

---

### Post by bobplano on 2007-09-28
you can install dapper and make your life installing ubuntu easier. dapper puts grub on the drive that you install it on, while fiesty and edgy don't do this. you can change where grub is installed in the two newer versions with sudo grub-install, but i don't know what else it needs. anyway someone else might see it and know what syntax needs to be used. then you can install fiesty or edgy.

---

### Post by logos34 on 2007-09-29
> **pcostanza said:**
>  What's the best way to do this and not have grub on the  XP/Vista system at all?  Any guides I can follow?

[http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/](http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/)
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811) 
(post #502)

---

### Post by pcostanza on 2007-09-29
Thanks very much for the info.  I'll do some reading on the subject before I take the plunge.

---

