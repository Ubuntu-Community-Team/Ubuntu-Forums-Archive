---
title: "Display settings for the text interface?"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-05-24
I use a LCD and everything looks fine when Xubuntu is at the log-on screen or the desktop, etc, everythings correctly installed, but I've noticed that the boot screen and text and pretty much anything on the command-line only interface looks horrible on the LCD (I've only recently upgraded to one), the terminal and anything within the GUI looks fine, but if I go back to just a bare-bones command line/terminal only it looks horrible, I remember reading somewhere there was something in one of the config files that can fix it?

---

### Post by Mustard on 2006-05-24
Can you elaborate on 'horrible'?

You could try adding vga=771 to your kernel boot options in the grub menu.lst.

---

