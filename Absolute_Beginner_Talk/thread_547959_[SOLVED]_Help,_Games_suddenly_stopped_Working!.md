---
title: "[SOLVED] Help, Games suddenly stopped Working!"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Ant_Merlin on 2007-09-10
Hello, I am very much a newby for Ubuntu and linux in general, I have installed Feisty on a dual boot and have installed compiz-fusion. everything has been fine until now. I have added a new user, and tried to change the splash screen, uninstalled Kiba-dock (got fed up with it) and now half my games wont work. Games like Lbreakout2, neverball, neverput, wormux and many more.

I have tried running them from a terminal with various switches (-nosound, -fullscreen etc) but to no avail. Any ideas anyone?

I also get random lockups after login, if I reset Xserver its usually ok, I have tried running in gnome rather than XGL but nothing seems to help.

---

### Post by Beggar on 2007-09-10
First of all, nice avater.

Now, what happens when the programs "wont work"? Do you get an error message, do they open the close quickly, etc. Also have you tried turning compiz-fusion off? 

These random lock ups, when did they start, are there any log messages after you restart?

```

sudo more /var/log/syslog
sudo more /var/log/Xorg.0.log

```

Note that the name of the x log will be different depending on which display it is running on, you will need to look in the var log folder, it could be running on another display, so instead of 0 it will be Xorg.1.log, etc.

---

### Post by Ant_Merlin on 2007-09-11
Hi I have run those log files but cannot find any errors or unusual log entries except for this in Xorg.0.log:


drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/f
glrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0

In regards to the programs, some of these open a blank window that will not close unless you  kill it in system monitor. Others just dont seem to do anything other than the sound of the hard drive loading a file.

I have tried running in Gnome rather than gnome XGL but no luck.

These lockups are usually when i try and logout and login as another user but sometimes when i boot, basically you get background colour from the login screen and sometimes a black or white box a quarter of the screen in size, also blank.

any ideas?

---

