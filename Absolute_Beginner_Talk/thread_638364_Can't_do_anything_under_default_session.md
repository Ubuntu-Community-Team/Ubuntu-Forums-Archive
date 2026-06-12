---
title: "Can't do anything under default session"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by eallan on 2007-12-11
Nothing opens under my old username and password.

I click and it says starting and nothing ever happens. However i can run under failsafe.


(process:6459): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:6463): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: present. 
xauth: (argv):1:  bad display name ":0" in "nextract" command
No matches found, authority file "-" not written
xauth: (argv):1:  bad "add" command line
Starting Xgl with options:  -accel xv:fbo -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
AUDIT: Tue Dec 11 22:22:07 2007: 6512 Xgl: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server

Xlib: No protocol specified


xmodmap:  unable to open display ':1'
AUDIT: Tue Dec 11 22:22:07 2007: 6512 Xgl: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server

Xlib: No protocol specified



(x-session-manager:6456): Gtk-WARNING **: cannot open display:  


There is my error log. I'd appreciate any help.

---

### Post by ajmorris on 2007-12-11
hi there,
have you tried re-installing the xorg server?

---

### Post by eallan on 2007-12-12
Using what command? 

I've reinstalled ubuntu-desktop and ran envy and let it auto configure the X.org.


edit: Just tried to reinstall it though the Synaptic Package manager with no luck. Same problem.

---

