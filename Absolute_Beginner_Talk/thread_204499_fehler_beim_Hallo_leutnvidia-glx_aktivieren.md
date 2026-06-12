---
title: "fehler beim Hallo leutnvidia-glx aktivieren"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by knorg on 2006-06-27
Good day

A few daysago I installed Ubuntu for the first time. When activating nividia-glx following error massage occoured:

knorg@workstation:~$ glxinfo | grep rendering
Error: couldn't find RGB GLX visual
knorg@workstation:~$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
knorg@workstation:~$

I tried the command, everything worked after that, but after the next restart the desktop couldn´t be loaded again. 

I use the amd64 version of the OS.
Hardware:
Dell precision 380
Grafikkarte: nvidia quadro 1400fx
CPU: Intel 830D
Chipsatz: Intel 955X
Für Hilfe bin ich sehr dankbar.

mfg
markus

---

