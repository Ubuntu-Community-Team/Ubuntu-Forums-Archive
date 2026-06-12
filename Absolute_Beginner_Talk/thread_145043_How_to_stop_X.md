---
title: "How to stop X"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by stardash on 2006-03-15
I am trying to install the drivers for my nvidia 7800gs. I need to get to just command line to stop X so I can install it. Anyone know how?

---

### Post by astyanax on 2006-03-15
You don't need to stop X to install the nvidia drivers.  This is all you have to do:

```
sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then open the xorg.conf file:
```
sudo nano /etc/X11/xorg.conf
```

- Change the Driver “nv” value in the “Device” section to Driver “nvidia”

Then restart X.  (CTRL+ALT+BACKSPACE)

Then you should be using the proprietary nvidia drivers.

---

### Post by arnieboy on 2006-03-15
to stop X do the following:
Ctrl-Alt-F1
log in with your user name.
then do```

sudo /etc/init.d/gdm stop
```

---

