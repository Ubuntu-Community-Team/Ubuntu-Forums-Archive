---
title: "beryl on intel 950 gma edgy"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by SMS on 2007-03-10
hey guys
just installed beryl on my laptop but when i start it i get this is my terminal

sms@sms-laptop:~$ beryl-manager
sms@sms-laptop:~$ libGL warning: 3D driver claims to not support visual 0x5b
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x5b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x5b
Reloading options

sms@sms-laptop:~$ Reloading...

(emerald:5951): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)' failed
Reloading...

(emerald:5951): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)' failed

---

### Post by igknighted on 2007-03-10
These are all normal outputs.  Is there an issue with beryl when it is running?  Most programs you launch via terminal will give some kind of debug output like this (especially KDE apps unless you specifically turn it off)

---

