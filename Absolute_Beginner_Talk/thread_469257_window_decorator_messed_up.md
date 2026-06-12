---
title: "window decorator messed up"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by shanike on 2007-06-09
i'm running beryl for window management and i use GTK for window decorating. everything worked fine until now - title bars and window borders are missing! i've tried reloading the window decorator, window manager, restarting.. changing window manager to whatever else but beryl fixes the problem, but i want my beryl... :(

[IMG]http://img132.imageshack.us/img132/9210/nowindowbordersef4.png[/IMG]

---

### Post by ggaaron on 2007-06-09
Run berlyl-manager form a terminal to see the errors.

---

### Post by shanike on 2007-06-10
```
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
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x3a00225 to texture
beryl: No GLXFBConfig for depth 32

```

---

### Post by ggaaron on 2007-06-10
Hmm, if I remember well, then beryl only works with 24bit depth - change it in /etc/X11/xorg.conf or probably in some X control utility.

---

### Post by shanike on 2007-06-10
i've managed to fix it by reloading a backed-up xorg.conf (which i was trying to edit to fix kernel 2.6.20-16-generic).

---

