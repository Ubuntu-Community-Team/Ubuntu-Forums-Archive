---
title: "Error: GTK Won't Initialize. Setuid Error. Can't Log Into Gnome"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by klausner on 2007-12-19
Ever since the recent security updates, I can't start a normal Gnome session. The .xsession-errors file says:

```
(process:6008): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6012): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
xauth: (argv):1:  bad display name ":0" in "nextract" command
No matches found, authority file "-" not written
xauth: (argv):1:  bad "add" command line
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
AUDIT: Tue Dec 18 17:13:39 2007: 6073 Xgl: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

xmodmap:  unable to open display ':1'
can't lock memory: Cannot allocate memoryWARNING: not using secure memory for passwords
AUDIT: Tue Dec 18 17:13:40 2007: 6073 Xgl: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

cannot open display: 
Run '/usr/bin/seahorse-agent --help' to see a full list of available command line options.
```

There is another thread on this at [http://ubuntuforums.org/showthread.php?t=627339]("http://ubuntuforums.org/showthread.php?t=627339"), but it hasn't produced the answer.

How do I edit/replace the GTK login events to try and find/eliminate the culprit? FWIW, I searched the entire disk for setuid setgid programs, and don't see anything suspicious.

---

### Post by klausner on 2007-12-19
Well it broke with a security update, and now, today's update seems to have fixed things. Seems like Beta testing on Gutsy has gone way downhill.

---

