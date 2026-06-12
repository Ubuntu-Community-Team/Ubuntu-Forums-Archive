---
title: "Help! Cannot log in normally"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by anhhung on 2007-10-23
When loggin I received the following messages:

1. Your session will last for 10s... plz use failsafe.
2. Below is the error message:

(process:7318): Gtk-WARNING **: This process is currently running setuid or set$
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:7322): Gtk-WARNING **: This process is currently running setuid or set$
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...

Missing xvnkb core: xvnkb.so.0.2.9!

Loggin in via failsafe is OK but I certainly dont want to do it forever!

Is there any way to solve this? Any help is appreciated!

---

### Post by akira777 on 2007-10-29
go to search for files, and type in "xvnkb" and delete the startup script from X11.  The best thing is to get rid of everything that relate to xvnkb.  If you are using Gutsy and compiled xvnkb, then it will not work.

---

### Post by quanghm on 2007-11-15
What method did you use to install xvnkb? if you use dpkg, then try dpkg --purge xvnbn. I tried and that worked for me. Otherwise, try to delete content of /etc/ld.* .

---

