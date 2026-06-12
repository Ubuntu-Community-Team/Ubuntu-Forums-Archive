---
title: "nvidia driver installation"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by hnaamyilkemku on 2006-10-30
i tried installing the nvidia-glx package that is described in this part of the ubuntu intro: 
   [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

it apparently installed, but i cannot successfully execute the following in order to activate the driver: 

  sudo nvidia-glx-config enable 

i get this message: 

  Error: your X configuration has been altered.
  This script cannot proceed automatically. If you believe that this
  not correct, you can update the md5sum entry executing the following
  command:
  md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
  otherwise edit manually /etc/X11/xorg.conf to change the Driver section
  from nv to nvidia.

how can i get the driver to work?

---

### Post by Perfect Storm on 2006-10-30
```
nano /etc/X11/xorg.conf
```

now change "nv" to "nvidia"

save and exit.

Restart X (ctrl+alt+backspace)

---

