---
title: "i have a question about KDE"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2008-04-15
i have ubuntu 7.04, and what if i wanted Kubuntu, without reinstalling ubutnu, i thin, is a there is a way im on windows xp right now, but i wanna remove it, soooo thanks for the help.

=== MaX

---

### Post by Crafty Kisses on 2008-04-15
Do the following in the Terminal

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

During the installation process, you should be asked whether you want to use KDM or GDM as your default display manager. If you think you'll use KDE more frequently, make KDM your default. If you think you'll use Gnome more frequently, keep GDM as your default, if you still want to use Ubuntu.

The default can always be changed later by modifying the default manager file: ```
/etc/X11/
``` For KDM, the file should read ```
/usr/bin/kdm
``` for GDM, the file should read ```
/usr/sbin/gdm
```

Then if you don't want KDE, you can always remove it by doing the following:
```
sudo aptitude remove kubuntu-desktop
```

---

### Post by Inxsible on 2008-04-15
> **LiNuXxToOthEMaX said:**
> i have ubuntu 7.04, and what if i wanted Kubuntu, without reinstalling ubutnu, i thin, is a there is a way im on windows xp right now, but i wanna remove it, soooo thanks for the help.

=== MaXI am not really sure i understand your question. Do you have ubuntu installed and want to install Kubuntu ?

in that case you can log into Ubuntu and run this command in a terminal```
sudo aptitude install kubuntu-desktop
```

EDIT: Too Late :P

---

### Post by SunnyRabbiera on 2008-04-15
or you can install KDE without Kubuntu, there are folks who use KDE on ubuntu without having to re install a thing

---

