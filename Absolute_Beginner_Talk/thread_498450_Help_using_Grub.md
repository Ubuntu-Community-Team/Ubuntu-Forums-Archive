---
title: "Help using Grub"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by joeRobee on 2007-07-11
I found a solution to one of my problems earlier while I was trying to install Ubuntu 7.04 that said to add the text acpi=off to my boot options line during the Ubuntu live cd startup scree to allow me to boot to the live cd.  That solution worked perfectly and the live cd booted great and I have it installed.  My problem is that I can't figure out how to save this text to my boot options to boot every time.  I have had to use Grub to add the text to the kernel each time I boot up.  Does anyone know what directory I can go into to save this to my boot options so I don't have to add it every time?

---

### Post by S15_88 on 2007-07-11
go to terminal type sudo nautilus then a window will pop up and just search for boot.lst i'm not 100% sure where it is i don't have my laptop handy, it's in the boot folder but i don't remember what folder that's in haha sorry.

hope that helps you a little. Thanks, Alain

---

### Post by jyba on 2007-07-11
The file you want to edit is /boot/grub/menu.lst

---

### Post by S15_88 on 2007-07-11
there ya go that's the one!  thanks jyba 

Thanks, Alain

---

### Post by joeRobee on 2007-07-11
Alright thanks

---

### Post by sugarland2k on 2007-07-11
Grub is quite interesting.  I became interested in some of the more advanced configuration for booting multiple partitions.  See [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)  for more information.

Friends do not let friends run Vista!

---

