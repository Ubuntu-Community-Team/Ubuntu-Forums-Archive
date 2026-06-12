---
title: "Beryl Error"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by djlyx on 2007-01-23
I tried to initiate beryl, and it works.  However this comes up when I load it:

djlyx@djlyx-desktop:~$ beryl-manager
djlyx@djlyx-desktop:~$ libGL warning: 3D driver claims to not support visual 0x4b

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(beryl-manager:6774): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6840): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
texture_from_pixmap Present
libGL warning: 3D driver claims to not support visual 0x4b
Reloading options
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
Initiating splash

Just so you know, I have an ATI Card

What does all this stuff mean?

Thanks

---

### Post by dbbolton on 2007-01-23
well, since you said that it does work, i would just add 'beryl-manager' to your start-up scripts ( system > prefs > session > startup )

it won't run from the terminal in that case, and shouldn't give you an error.

---

### Post by djlyx on 2007-01-24
It is running kinda slow and laggy.  Is it possible that beryl is running without taking advantage of the video card's hardware acceleration?

---

### Post by KumoriJinsoku on 2008-01-03
[http://ubuntuforums.org/showthread.php?p=2204087](http://ubuntuforums.org/showthread.php?p=2204087)

---

