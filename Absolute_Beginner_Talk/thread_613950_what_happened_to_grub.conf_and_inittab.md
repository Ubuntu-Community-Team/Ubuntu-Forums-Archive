---
title: "what happened to grub.conf and inittab?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2007-11-15
what happend to these files? i cant even locate them with whereis [filename]..

---

### Post by taurus on 2007-11-15
/boot/grub/menu.lst.

---

### Post by oldos2er on 2007-11-15
They don't exist in Ubuntu. grub.conf is /boot/grub/menu.lst, and inittab function is replaced by something called Upstart. See [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by Fittersman on 2007-11-15
that upstart thing... how would i use it to change the default runlevel? because when i boot my computer it boots into text mode and i have to type startx everytime to get the GUI instead of it starting automatically. I also cannot shutdown the computer from the shutdown button, there is no option for it, i can only log out (which takes me back to text mode)

---

### Post by taurus on 2007-11-15
In System -> Administration -> Services, make sure you put a check mark for gdm so it will start, GUI login screen, when you boot Ubuntu.

---

