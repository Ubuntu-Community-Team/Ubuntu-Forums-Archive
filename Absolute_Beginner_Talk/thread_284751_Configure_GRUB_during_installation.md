---
title: "Configure GRUB during installation"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by newbietolinux on 2006-10-26
I want to make my Windows XP system dual boot with Ubuntu. I want to make Windows the default OS to boot up after 10seconds. But I couldn't find any option to make Windows the default OS booting up when installing Ubuntu. How can I make Windows the default OS booting up when installing Ubuntu? Can I edit GRUB to make the change to my system now? 

Is there a way to configure our boot loader when we are installing Ubuntu?

---

### Post by nickpaton on 2006-10-26
Have a look at this:

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by studentism on 2006-10-26
I don't think there's an option during install.  Once Ubuntu is installed and you've actually booted into the system, edit (as root) /boot/grub/menu.lst and find the option for "default".  It starts numbering at zero, so change it to the value on the initial boot list that corresponds to your Windows partition.

If you're not comfortable with a commandline editor, you can get a graphical one through
```
gksudo gedit /boot/grub/menu.lst
```

Grub can be edited during boot, so if you mess something up just google around for correct settings (ie don't worry about rendering your system unbootable with this).


edit: beaten

---

