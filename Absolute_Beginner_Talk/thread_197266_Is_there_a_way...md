---
title: "Is there a way.."
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2006-06-15
I install JUST the XFCE (or KDE, etc.) windows manager without all of the added applications?

---

### Post by aysiu on 2006-06-15
Yes.

Do a server install from the Alternate Install CD.

When you login at the command prompt, just type ```
sudo aptitude update
sudo aptitude install xfce4
```

---

### Post by bluevoodoo1 on 2006-06-15
For KDE, install the "kde-core" package.

and 

for xfce I believe it's the "xfce4" package.

---

### Post by aysiu on 2006-06-15
For an absolute barebones KDE, don't you install *kdebase*?
> 
base components from the official KDE release

KDE (the K Desktop Environment) is a powerful Open Source graphical desktop environment for Unix workstations. It combines ease of use, contemporary functionality, and outstanding graphical design with the technological superiority of the Unix operating system.

This metapackage includes the nucleus of KDE, namely the minimal package set necessary to run KDE as a desktop environment. This includes the window manager, taskbar, control center, a text editor, file manager, web browser, X terminal emulator, and many other programs and components. 

---

