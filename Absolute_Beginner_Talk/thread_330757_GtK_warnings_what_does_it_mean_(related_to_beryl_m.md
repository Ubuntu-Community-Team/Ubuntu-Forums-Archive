---
title: "GtK warnings what does it mean? (related to beryl mb)"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Skyler0 on 2007-01-03
I've got it with some other programs and stuff when running it, but here's 2 examples:
This is from checkgmail, and gmplayer

> Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/bin/checkgmail line 381.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/bin/checkgmail line 381.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/bin/checkgmail line 381.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/bin/checkgmail line 381.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/bin/checkgmail line 381.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/bin/checkgmail line 381.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/bin/checkgmail line 381.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/bin/checkgmail line 381.
Creating translations file at /home/sky/.checkgmail/lang.xml ...
Updating translations file ...
Wide character in print at /usr/bin/checkgmail line 3485.
 ... done!


> Failed to open LIRC support. You will not be able to use your remote control.

(<unknown>:14877): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:14877): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:14877): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:14877): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:14877): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:14877): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:14877): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:14877): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Xlib:  extension "XFree86-VidModeExtension" missing on display "localhost:1.0".


It always has to do with pixmaps.

Thanks.

---

### Post by evilmike on 2007-01-04
You are most likely getting this problem because you installed a theme without having the appropriate packages that is uses. I believe the one you are missing is  gtk2-engines-pixbuf.

Try
```
 sudo apt-get install gtk2-engines-pixbuf 
```
and see if that fixes the problem. I had a similar problem with a theme I was using, and this fixed it up.

---

### Post by exc220 on 2007-01-27
hi i've tried your solution and it works!

thanx!

---

### Post by Bashed on 2007-05-07
I had that already installed and was still getting the errors

```
chad@Secured:~$  sudo apt-get install gtk2-engines-pixbuf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk2-engines-pixbuf is already the newest version.
The following packages were automatically installed and are no longer required:
  libktnef1 libberylsettings0-gconf blt koffice-libs tcl8.4 tk8.4 libgpgme11
  koffice-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

What should I do?

---

