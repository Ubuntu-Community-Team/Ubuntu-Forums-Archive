---
title: "urgent help plz, am stuck !!!"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-06-02
i have edited the file /etc/X11/xorg.conf to disable my laptop touch pad by adding # to one of the section so now it looks like this :

#Section "InputDevice"
# Identifier "Synaptics Touchpad"
# Driver "synaptics"
# Option "SendCoreEvents" "true"
# Option "Device" "/dev/psaux"
# Option "Protocol" "auto-dev"
# Option "HorizScrollDelta" "0"
#EndSection

i rebooted the system but it failes launching the interface, am poor with terminal commands so what is the command to open /etc/X11/xorg.conf and remove the # characters which i have added ???

---

### Post by seshomaru samma on 2007-06-02
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by m!key on 2007-06-02
Hey,

```
sudo nano /etc/X11/xorg.conf
```

Once done press CTRL + X to exit, Y to save and enter.

---

### Post by m!key on 2007-06-02
Darn...

Too late :p

---

### Post by ugm6hr on 2007-06-02
If you still want to disbale the Tap to Touch function:
[http://ubuntuforums.org/showthread.php?t=421236](http://ubuntuforums.org/showthread.php?t=421236)

---

