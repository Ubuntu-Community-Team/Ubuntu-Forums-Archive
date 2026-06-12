---
title: "REMOVING DRIVERS: so you can start over. (nvidia)"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by deltapapazulu on 2006-10-03
i have tinkered with a few methods of installing nvidia drivers.  tried the one from nvidia's site and the ones in the ubuntu package.  Here is what I would like to do.  Restore the system to its prestine pretinkered state.  And start over installing the Nvidia Accelerators downloaded from Nvidia's site.

i want to start over from scratch and role back previous attempts.

i am a total noob

---

### Post by tseliot on 2006-10-03
Read Method 2 of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Josh1 on 2006-10-03
> **deltapapazulu said:**
> i have tinkered with a few methods of installing nvidia drivers.  tried the one from nvidia's site and the ones in the ubuntu package.  Here is what I would like to do.  Restore the system to its prestine pretinkered state.  And start over installing the Nvidia Accelerators downloaded from Nvidia's site.

i want to start over from scratch and role back previous attempts.

i am a total noob

In terminal (ctrl+alt+f1):
```

sudo dpkg-reconfigure -phigh xserver-xorg
startx

```
This will remove the drivers.

installing nvidia driver (You can now do this in the terminal in kde/gnome:

```

sudo aptitude install nvidia-glx
sudo gedit /etc/X11/xorg.conf

```
in Section "Device" change "nv" to "nvidia"

restart x: <ctrl> + <alt> + <backspace>.

Goodluck,
Josh

---

