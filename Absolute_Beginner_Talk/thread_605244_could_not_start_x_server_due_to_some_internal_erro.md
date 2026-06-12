---
title: "could not start x server due to some internal error? HELP"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2007-11-06
help!!

Edit:  SOrry about that but my computer wouldn't let me view topics similar, i didn't mean to save it.

EDIT: STILL NEED HELP. I ran a failsafe gnome session and it worked. What do I do from here to diagnose and fix the problem?

---

### Post by Dr Small on 2007-11-06
We will definitatly need some more information than just that...

---

### Post by Happy_Man on 2007-11-06
Uhm.... we're going to need a bit more information. Remember, we can't see your computer screen. Could you please copy the error down on a sheet of paper or something, and then type it up here so we can have a look at it?

---

### Post by Evil Wayz on 2007-11-06
> **Happy_Man said:**
> Uhm.... we're going to need a bit more information. Remember, we can't see your computer screen. Could you please copy the error down on a sheet of paper or something, and then type it up here so we can have a look at it?

the display has been disabled it reads:

could not start xserver due to some internal error.  GDM has been disabled.

Then it tried to run something called fsck and then told me to do it manually and a god awful list of inodes were wron gor something. Then i reboted. 

I tried the dpkg-reconfigure commands and it said that xserver.org doesn't exist. 

now i cant get to my boot login screen but then it gos black and then goes right back to my boot screen again!

EDIT: Failsafe gnome works. What do i do now?

---

### Post by Evil Wayz on 2007-11-06
BUMP

I ran a failsafe gnome session. what can i do from here to make my system work normally?

---

### Post by Evil Wayz on 2007-11-06
this is what my xserver.error file says. IT shold be noted that i have an ati card not an Nvidia


(process:6186): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:6190): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
[0] couldn't create glitz drawable for window

Fatal server error:
no screens found
rm: cannot remove `/tmp/.X1-lock': No such file or directory
xmodmap:  unable to open display ':1'

(x-session-manager:6183): Gtk-WARNING **: cannot open display:

---

### Post by Happy_Man on 2007-11-07
Hmm.... I get this error also, whenever I try to run KDE 4 as a session. This is quite interesting.... have you tried installing a different DE and seeing if that works all right?

---

### Post by Evil Wayz on 2007-11-07
> **Happy_Man said:**
> Hmm.... I get this error also, whenever I try to run KDE 4 as a session. This is quite interesting.... have you tried installing a different DE and seeing if that works all right?

I tried kubuntu desktop and now i get stuck in low graphics mode, and either the graphics card is in use but the driver is disabled OR the graphics card is NO in use and the driver is enabled. Oh and get this:  Gnome failsafe session runs with the correct driver in the correct resolution. Default session jsut keeps cyclign back to the boot login screen.

---

### Post by Happy_Man on 2007-11-07
Have you tried going into the System Settings in KDE (K menu --> System Settings) and changing your monitor resolution? If you can, it's just that KDE isn't autodetecting your res, and if you can't, it may be a driver problem.

---

### Post by Evil Wayz on 2007-11-07
If a failsafe session works perfectly, couldn't I just copy teh contents of the .failsafe files to the originals and then the default would work?

If so what files should I modify?

---

