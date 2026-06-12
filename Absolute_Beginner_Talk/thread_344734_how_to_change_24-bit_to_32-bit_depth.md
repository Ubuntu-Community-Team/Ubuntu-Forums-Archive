---
title: "how to change 24-bit to 32-bit depth??"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by TheNemeses on 2007-01-23
ok well a month back i was messing with xorg.conf and messed it up so i had to redo it, but my graphics are all messed up and i was looking at the file again and my resolution is fine but it says the default dept is 24... so i switched to 32 and it crashed again so i had to re-do it. how do i fix this?

---

### Post by MadmanTM on 2007-01-23
Questions : 

- did you update your drivers ?
- what kind of card you are using? (Nvidia, ATI)

looks like it could be a driver issue...

---

### Post by Shatrat on 2007-01-23
24 bit is 32 bit.
32 bit is actually 24 bit color and 8 bit alpha.

---

### Post by igknighted on 2007-01-23
> **TheNemeses said:**
> ok well a month back i was messing with xorg.conf and messed it up so i had to redo it, but my graphics are all messed up and i was looking at the file again and my resolution is fine but it says the default dept is 24... so i switched to 32 and it crashed again so i had to re-do it. how do i fix this?

So far as I know linux doesn't support 32 bit color (which is ok because it's basically the same as 24 bit)

---

### Post by MadmanTM on 2007-01-23
> **igknighted said:**
> So far as I know linux doesn't support 32 bit color (which is ok because it's basically the same as 24 bit)

this could explain why UT2004 would freeze when i switched resolutions in 32bit and when i tried in 16 it worked fine :p

---

### Post by TheNemeses on 2007-01-23
nvidia 6800, but i can see like display textures not being in true color, kinda like in windows if you change the depth you can see the color or lack of color actually, and this is only happening after it crashed the first time.

---

### Post by Shatrat on 2007-01-23
It may have defaulted back to a lower setting after the crash.
Try going into the xorg.conf and changing the default depth back to 24.
To do that, gksudo gedit /etc/X11/xorg.conf
Look for Section "Screen"
make sure there is a line that says
   DefaultDepth    24

---

### Post by TheNemeses on 2007-01-23
thats what its already at, thats what im sayin.

---

### Post by pickarooney on 2007-01-23
When I try to run Second Life it complains that the colour depth is not set to 32. When I change it in xorg.conf from 24 to 32 X won't start. Is there some sort fo workaround or is this an impossible circle?

> 
Unable to create window, be sure screen is set at 32-bit color and your graphics driver is configured correctly.  See README-linux.txt for further information


---

### Post by TheNemeses on 2007-01-23
yeah seriously this is realllly annoying, maybe there are some new drivers i can download? any help?

---

### Post by bry5an on 2007-05-24
so i changed it from 24-bit to 32-bit and found that x server won't load now.. how can i load the xorg.conf file to edit it in the shell? plix halp! thx!:cry:

---

### Post by Junixx on 2007-05-24
```
sudo nano /etc/X11/xorg.conf 
```


Thats what I usually use

---

### Post by Outrunner on 2007-05-24
As I belive was stated previously, Linux does not support 32bit because 32bit is actually 24bit +  alpha channel:

[http://en.wikipedia.org/wiki/32-bit](http://en.wikipedia.org/wiki/32-bit)

---

### Post by bry5an on 2007-05-24
> **Junixx said:**
> ```
sudo nano /etc/X11/xorg.conf 
```


Thats what I usually use

thanks that worked =)

and yes, i saw that ubuntu doesn't support 32-bit.. but i had to see for myself :p

---

### Post by rabbitnightmare on 2008-05-06
Actually there is a humongous difference between 24 and 32 bit...
Well, there are technical differences. In 32-bit mode, all pixels are aligned on 32-bit boundaries, which makes it easier to optimize drawing operations, since you can just work with double-word operations. Thus, the video card does differ between 24-bit modes and 32-bit modes, although even if you use a 32-bit mode, you still only get a 24-bit colorspace.

Also, in more advanced applications, like texture drawing acceleration and such things, the last 8 bits are used to represent an alpha channel (that is, gradual translucency), but that doesn't apply to this discussion.

For the end user, however, a 24-bit mode gives exactly the same visual quality as a 32-bit mode. If anything, a 32-bit mode can be faster than a 24-bit mode. In general, however, they are extremely similar.

You can, in Linux, as I have done it, enable 48 and 64 bit color modes. This mode makes rendering things work extremely fast and there is no digital dithering. You can see digital dithering it looks like squares. Usually most visible on black going to darker black. To me this is extremely annoying. Once enabled there is no matrix visible to the human eye and adds a whole heck of a lot more shading per pixel. Doing this, however, needs a higher end video card and needs you to know how to edit files in the kernel level. 

32 is not a valid depth not even in Windows. When running in 32 bit in Windows it actually is running in 24 bit color mode calling 32 bit code from the kernel. Like running a 32 bit application. It emulates the Alpha channel and doesn't display it on most video cards but instead down-samples it. However if 32 bit is able I don't see why they don't just go to 48 

If you were to actually be able to see alpha colors air would be solid and we would all be blind as the Sun's rays would bounce off the particles accelerating them into sort of a green tint.

---

