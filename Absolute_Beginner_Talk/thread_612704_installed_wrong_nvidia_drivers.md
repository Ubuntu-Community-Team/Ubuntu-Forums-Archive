---
title: "installed wrong nvidia drivers"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by krementz on 2007-11-14
I chose to install the nvidia drivers, and now I have a corrupted video so I can't get to the GUI. User error.

Anyway,I can boot to the command line. What do I do to restore the original driver?

Thanks from a newbie.

---

### Post by carlosjuero on 2007-11-14
from the command line ```
sudo dpkg-reconfigure --phigh xserver-xorg
```
This will force a reconfiguration of the display drivers, allowing you to choose a different one from a list and then re-writing the xorg.conf file

---

### Post by KhaaL on 2007-11-14
do you know what the package name was?

if you can use the command line conviently, edit /etc/X11/xorg.conf and search for the string:

        Driver          "nvidia"


Change "nvidia" to "nv" and I think you'll be able to get back to the GUI.

Make sure to make a backup first by typing:
cp /etc/X11/xorg.conf ~/xorg.conf.backup

EDIT: Carlos suggestion is better (i think - i haven't tried it myself! :p )

---

