---
title: "Inspiron 1720 help !"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by florescu109 on 2008-01-31
I have a very slow touchpad. I tryed to change the settings but I have a maximum speed in the mouse menu. Can anybody halp me ? It must be a command to access the settings. It is anoying to move the cursor so slowly.

---

### Post by iAtari on 2008-02-01
Try this: [http://www.compass.com/tpconfig/tpconfig-3.1.3.tar.gz](http://www.compass.com/tpconfig/tpconfig-3.1.3.tar.gz)

Sounds like a needed touchpad driver.

---

### Post by kpkeerthi on 2008-02-01
You have to enable/tweak synaptics settings in Xorg.conf. See [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Additional_Settings](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Additional_Settings)

---

### Post by jan quark on 2008-02-01
you enter the file by typing into the terminal

```
sudo gedit /etc/X11/xorg.conf
```

and thats how my synaptic configuration looks like I have a dell 1501

> Section "Input Device"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

---

