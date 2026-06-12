---
title: "Am I on the right track as far as Installing the Cairo Dock?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-25
[CENTER][COLOR="Green"][FONT="Palatino Linotype"][SIZE="4"]Would any of you be patient enough to please help me & others who don't quite understand exactly how to install the Cario Dock on our computers. In my case, I'm using a Dell Inspiron 531s which is installed with Ubuntu 7.10 (Gusty Gibbons) it has a built-in NVidia video card (drivers included) and it's running on the AMD64 (64Bits) system?

I'll start by highlighting the problems I've been having with the installation-instructions (which I have listed 1-2):

Instruction #1:[/SIZE][/FONT][/COLOR][/CENTER]
**1.** Download the latest cairo-dock 32bit deb files. You need two deb files, one called **cairo-dock_vX.X.X.X_i686-32bits.deb** and the other **cairo-dock-plug-ins_vX.X.X.X_i686-32bits.deb** (where the X's represent the latest version number, 1.5.0.1 at the time of writing this) from _[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)_ to your home folder.
[IMG]http://img141.imageshack.us/img141/4687/0wenttoberliosdeveloperer1.png[/IMG]

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]I successfully installed those 2 .deb-files: cairo-dock-plug-ins_v1.5.1_i686-32bits.deb &  cairo-dock_v1.5.1_i686-32bits.deb, however I don't know how to properly install cairo-dock-sources-20080219.tar.bz2. 

If any of you know how to install the Cairo Dock, would you please give me step-by-step instructions about what I should do with this package/file: cairo-dock-sources-20080219.tar.bz2?[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #2:[/SIZE][/FONT][/COLOR][/CENTER]
**2.** Open a terminal screen and run
```
sudo dpkg -i --force-all cairo-dock*.deb
```

[color="green"]**That command worked fine for me, in the Terminal.**[/color]

```
sudo getlibs /usr/bin/cairo-dock
``` (see prerequisite 3 above if this results in an error)

[color="green"]**And that terminal-command worked fine for me.**[/color]

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"] I'd appreciate any future-help given to me, in this case.[/SIZE][/FONT][/COLOR]

---

### Post by overdrank on 2008-02-25
HI and please do not make multiple threads on the same subject.
[http://ubuntuforums.org/showthread.php?t=707130](http://ubuntuforums.org/showthread.php?t=707130)
I have not install cairo on 64 bit but if you have installed the debs ( in your other thread) then you should not have to install by the tar. If you still having issues there is instructions on compiling on a 64 bit on this link
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

