---
title: "new Programs"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by bryan4134 on 2006-04-22
Just loaded Ubuntu and working fine.  I have now added some programs but only one or two of them appear on the menus (e.g. Adobe Reader). Most of others (e.g. Aegis virus scan) do not appear on the menus although everthing seems to be in order with the installation.  This is probably a very stupid question - but where are they??

Thanks, Bryan

---

### Post by aysiu on 2006-04-22
If a graphical program is packaged properly, it'll include a *programname*.desktop file with it.

That .desktop file is the menu entry. Unfortunately, some programs don't come with that entry--it's entirely up to the program's maintainer to include that entry in the package.

Even if the .desktop file exists, sometimes you have to refresh the menu for the entry to appear. In Gnome, you press Alt-F2 and type the command ```
killall gnome-panel
``` In KDE, the command is ```
killall kicker
```

And then... some programs are not graphical at all but command-line tools. These don't have a graphical menu entry because they cannot be launched graphically.

---

