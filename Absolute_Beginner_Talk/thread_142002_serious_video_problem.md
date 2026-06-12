---
title: "serious video problem"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-03-09
so i attempted to install the right drivers for my ati and somehow managed to mess up my system even worse.

so i looked at a few guides on here and must have done the wrong thing.

now, everytime i start the xscreen saver application, it always says xscreensaver is not set at 0.0 which it should be.

also
when i rebooted, i was not able to get into X untill i edited /etc/X11/xorg.conf and changed the pci locator of the ATI thing from 1.0.1 to 1.0.0

and then i rebooted and X started, but my monitor didn't accept it untill i did auto button on the monitor.

help me restore just my default video settings : (

---

### Post by mlind on 2006-03-09
you should run configuration wizard that will restore xorg.conf

```

sudo dpkg-reconfigure xserver-xorg

```

you should probably accept all defaults that wizard suggests,
unless you know what you're doing.

---

