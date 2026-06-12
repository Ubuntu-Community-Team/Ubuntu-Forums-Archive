---
title: "Gnome runs only in failsafe mode"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by uioreanu on 2007-11-13
Hello,

Since upgrading to gutsy at boot-time the screen paused and the only working session was Failsafe Gnome. I thought I can install KDE then, to overcome the Gnome problem I thought I have. Now after having both Gnome and KDE, at boot time the screen returns to the base login page after showing a failsafe warning and at the login page the only working session is the Failsafe Gnome. 

the .xsession-errors content follows:

```


(process:5794): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5798): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 

Fatal server error:
no screens found
rm: cannot remove `/tmp/.X1-lock': No such file or directory
xmodmap:  unable to open display ':1'
xsetroot:  unable to open display ':1'
xset:  unable to open display ":1"
xsetroot:  unable to open display ':1'
startkde: Starting up...
startkde: Running kpersonalizer...


```

can anybody help?

---

### Post by mikesignguy on 2007-11-13
it seems that you have Nvivdia drivers installed before you upgraded

Checking for nVidia: not present.

everytime you upgrade you need to install the drivers again

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver)

that is the quick answer .. there may be a few more issue but make sure you have the restricted drivers installed is a good start

---

### Post by Jeremy_Kyle_Vanhorn on 2008-03-11
i have the same prob. i did install my drivers then upgraded... but i dont have invida, i have ati.... any help on that?

---

### Post by mikesignguy on 2008-03-13
reinstall the drivers

if you use restricted drivers you need to reinstall them AFTER you update

---

