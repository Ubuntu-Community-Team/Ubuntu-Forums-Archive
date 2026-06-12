---
title: "Buttons are gone now that I installed Beryl"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by XLostSpartanX on 2007-01-27
So I installed Beryl last night and now this happened.

My buttons that are usually in the top right of the window are gone.

[IMG]http://i16.tinypic.com/43h39qs.png[/IMG]

---

### Post by Happy_Man on 2007-01-27
All right. Go right-click on the Beryl icon (red ruby-type gem thingy) in the top-right corner, and select "emerald theme manager". Pick a theme, and if all is well, your buttons will come back! :D

---

### Post by XLostSpartanX on 2007-01-27
> **Happy_Man said:**
> All right. Go right-click on the Beryl icon (red ruby-type gem thingy) in the top-right corner, and select "emerald theme manager". Pick a theme, and if all is well, your buttons will come back! :D
Ok.  I tried to pick a theme but when I click on it nothing happens.

---

### Post by JamieC on 2007-01-27
Right click the gem and choose 'Reload Window Manager' (and failing that 'Reload Window Decorator').

---

### Post by XLostSpartanX on 2007-01-27
> **JamieC said:**
> Right click the gem and choose 'Reload Window Manager' (and failing that 'Reload Window Decorator').

Still didn't work.

---

### Post by JamieC on 2007-01-27
Try restarting the X server by pressing (CTRL + ALT + BKSP) and then login again.

---

### Post by XLostSpartanX on 2007-01-27
> **JamieC said:**
> Try restarting the X server by pressing (CTRL + ALT + BKSP) and then login again.

That was the first thing I tried.  Didn't work either.

---

### Post by JamieC on 2007-01-27
Just to determine if beryl is the source of the problem, right click the gem once again. Then choose  'Select Window Manager', then choose Metacity.

---

### Post by XLostSpartanX on 2007-01-27
> **JamieC said:**
> Just to determine if beryl is the source of the problem, right click the gem once again. Then choose  'Select Window Manager', then choose Metacity.

My buttons came back when I did that.

---

### Post by JamieC on 2007-01-27
Right, so it's beryl or emerald that is the cause of the problem. 

Choose an emerald theme again (by clicking it (twice to be sure)). Then change the window manager back.

---

### Post by Cows on 2007-03-03
yea this is happening to me also, i had ATI Radeon 9200 PRO and everything was working ok, then today i upgraded my video card to nVidia GeForce 7600 GS and installed the nVidia drivers following this tutorial:

[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+beryl+edgy](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+beryl+edgy)

i install beryl and everything and the cube thing loads but my window decorator is gone. I also read another thread on this problem but they didn't solve it neither. here is the link to the other thread:

[http://www.ubuntuforums.org/showthread.php?t=349113&highlight=beryl+window+decorator+is+gone](http://www.ubuntuforums.org/showthread.php?t=349113&highlight=beryl+window+decorator+is+gone)

EDIT: This is the errors in gnome-terminal

```
cows@MoO:~$ beryl-manager
cows@MoO:~$ 
(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:8825): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
Initiating splash

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:8920): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32


```

---

### Post by Cows on 2007-03-03
i reinstalled the nvidia drivers and the beryl and it now works nicely =]

the tutorial the solved my problem was: [http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

it still says this but as long as it works its alright. although since now i got a nVidia 7600 GS the water effects and trailing water mouse should work when i press ALT + Super ( windows key) and or Shift + F9.

```
cows@MoO:~$ beryl-manager
cows@MoO:~$ 
(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6862): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6927): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options



```

---

### Post by deanl on 2007-03-03
I had the same problem.

If you're using an ATI card make sure you have XGL installed and running as your session. Another idea is to revert back to the previous version of Beryl.

---

### Post by Cows on 2007-03-04
well im not using xgl since idk how to install, currently i am reading to find out how though. also ubuntu is distributed with aiglx by default correct?

---

### Post by pveith on 2007-03-04
you might want to install the "heliador" windowdecorator, which uses gtk-themes in beryl. This should give you the windowframe back until emerald works again...

---

