---
title: "GLXGears"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by SIXAXIS on 2008-02-04
Hi again guys,

I wanted to see if the 3D acceleration of my video card was working after an install of drivers. (I wanted to check because I don't know if the driver install worked properly). I ran GLXGears under Ubuntu 7.10 and got around 700FPS. My computer and video card aren't that good (ATI Radeon XPRESS 200M <-- eww). With 700FPS, do you think that Linux is using full 3D acceleration or is it software emulating it with the CPU?

---

### Post by zarqoon on 2008-02-04
Did you use the standard window size?
If yes 700 frames is a little low and could be just the cpu. For comparison i get 13k with a 7800gt.
Try using
```
glxinfo | grep direct
```
There should be a line saying 
direct rendering: Yes

If it says no your driver is not working properly

---

### Post by Blutack on 2008-02-04
Try this:
> user@whatever:~$ glxinfo | grep -i direct
direct rendering: Yes
That is what mine returns, if yours does the same you should be fine, although from the sounds of that FPS score it's probably working fine anyway.

---

### Post by Blutack on 2008-02-04
Snap!
(Oh, and my Nvidia 7200 mobile thingy gets about 2000)

---

### Post by zarqoon on 2008-02-04
> **Blutack said:**
> Try this:

That is what mine returns, if yours does the same you should be fine, although from the sounds of that FPS score it's probably working fine anyway.

With 700 fps its definately not working fine. I dimly remember having about 1500 on a athlon 500 with a geforce 1 way back

---

### Post by Jerry N on 2008-02-04
Do you have the "effects" turned on, ie the Compiz-Fusion thing?  I find that overall performance (as well as GLXGEARS) on my Athlon 2400+ with 1gb and FX5500 takes a noticeable hit with the "effects" turned on.  I find the effects to be quite worthless so it doesn't bother me to leave them turned off.

Jerry

---

### Post by Blutack on 2008-02-04
> With 700 fps its definately not working fine. I dimly remember having about 1500 on a athlon 500 with a geforce 1 way back

ATi cards suck massively at GLXGears compared to Nvidia ones.  GLXgears isn't really a proper 3D benchmark anyway.  The glxinfo method is the only way to check properly really.

---

