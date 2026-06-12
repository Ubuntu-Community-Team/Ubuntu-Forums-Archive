---
title: "grub question"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by zib_redlektab on 2007-01-14
ok, i'm a real beginner here. I have a Dell Dimension something-or-other that I've out XP home edition, a cracked version of OS X, and (of course) ubuntu 5.04. I know, I should upgrade to 6.10 or whatever, but I'm using it for a gameserver that's only compatible with 5.04 and earlier (idk why, i think its because of the glibc version or something).

The problem is, when I boot up GRUB shows me my boot options, and OS X isn't on there. idk why this is, but does anyone know how to get it to display all of my partitions on the drive, or if there's another boot thingy i can use that'd do this?

thanks!

---

### Post by moshuptrail on 2007-01-14
There is a way to scan for OS's and create a new grub menu.  I can't remember now how to do that, but a little searching should yield results.

However, the grub menu is stored in /etc/grub/menu.list

If you know the location of your OS/X it should be fairly easy to add an entry to the grub menu.

must use sudo to edit it.  be careful though!
don't remove entries before you've tested the new ones

---

### Post by zib_redlektab on 2007-01-14
hmm...i don't seem to have a /etc/grub...:-k

---

### Post by zerhacke on 2007-01-14
The file is located in /boot/grub/menu.list

---

### Post by sailor2001 on 2007-01-14
places/computer/file system/boot/grub/menu.lst

---

### Post by zib_redlektab on 2007-01-14
awesome, i added osx to the menu with basically the same settings as xp, rebooted and it works just fine! thanks a ton!8) 
[IMG]http://farm1.static.flickr.com/157/353400147_d5398f27d7_o.jpg[/IMG]

---

