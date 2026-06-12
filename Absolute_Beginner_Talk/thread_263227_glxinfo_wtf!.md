---
title: "glxinfo wtf?!"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by dmichaels on 2006-09-22
drew@reborn:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


what the heck?!

---

### Post by kidders on 2006-09-22
Did you load the GLX extension?

---

### Post by dmichaels on 2006-09-22
uh no i havent...:oops: can u tell me how to do this?

---

### Post by kidders on 2006-09-22
No problem ...

Add this to your "Module" section in /etc/X11/xorg.conf. I think that should do it.
```

load "glx"

```

---

### Post by dmichaels on 2006-09-22
i have an nvidia NV36 5700LE i have load "glx"

is there more i can try doing?

---

### Post by dmichaels on 2006-09-22
ok ive tried HOWTO's from alot of sources and nothing is working. i really need help solving this issue. nothing has worked.

---

### Post by kidders on 2006-09-23
Are the HOWTOs you've tried Nvidia-specific? I used to have an Nvidia card ... afaik recent drivers have their own GLX driver bundled with them.

I may be *waaaaaaay* off (I wasn't using Ubuntu at the time), but for me, the trick was to disable the kernel's Nvidia drivers and use the (newer) ones from Nvidia itself.

---

