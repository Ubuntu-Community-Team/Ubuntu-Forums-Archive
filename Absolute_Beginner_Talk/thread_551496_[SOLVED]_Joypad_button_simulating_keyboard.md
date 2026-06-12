---
title: "[SOLVED] Joypad button simulating keyboard"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-09-15
I am playing Xmoto, incredible game btw, but it makes my arm hurts, so I tried to configure my usb joypad in the game but it didn`t accepted. So does anyone know how to makes the joypad simulates the keyboard keys??

Thank you...

---

### Post by mocoloco on 2007-09-15
I couldn't find anything in the repositories that does this.  I'm using an app called [xjoypad]("http://download.ammoq.com/"), command-line only but works great.
Then I have some shell scripts that set it up and launch the games for me.  For example here's one that launches frozen bubble in two player mode, after configuring the joystick to use the keys for the second player (I play it with my son, me on keyboard and him on js).
```
#/bin/bash
~/Downloads/xjoypad/xjoypad -device /dev/input/js1 -up 52 -down 56 -left 53 -right 55 -buttons 40 54 13 14 15 16 17 18 19 110 &
frozen-bubble -fs -di -cr
```

There was a second app I used to get the keycode numbers for each key, can't remember now, if I find it I'll post.
I'm surprised not to find any gui frontends to this.  Maybe I'll write one when I find the time...

---

### Post by felicity on 2007-09-15
Another good choice is rejoystick, here's a deb of it:
[http://superb-east.dl.sourceforge.net/sourceforge/rejoystick/rejoystick_0.3.3-1_i386.deb]("http://superb-east.dl.sourceforge.net/sourceforge/rejoystick/rejoystick_0.3.3-1_i386.deb")

---

### Post by mocoloco on 2007-09-16
> **felicity said:**
> Another good choice is rejoystick, here's a deb of it:
[http://superb-east.dl.sourceforge.net/sourceforge/rejoystick/rejoystick_0.3.3-1_i386.deb]("http://superb-east.dl.sourceforge.net/sourceforge/rejoystick/rejoystick_0.3.3-1_i386.deb")

Thanks felicity, rejostick is MUCH easier to set up and use.  My only complaint is creating multiple setting files.  The --help options says you can specify separate read / save files, but I can't get that option to work :(.

---

### Post by brunoskrebs on 2007-09-16
Yeah it worked perfect this rejoystick, thank you very much....

---

### Post by wounded on 2007-09-22
I am trying to make my gamepad map to my keyboard and found this (I was trying to use joy2key but was driving me homicidal) nd tried rejoystick but cannot get it to run D: 

```
[wounded:~]rejoystick
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


       ---------------------- DirectFB v0.9.25 ---------------------
             (c) 2000-2002  convergence integrated media GmbH  
             (c) 2002-2004  convergence GmbH                   
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-12-20 21:25) 
(*) Direct/Memcpy: Using MMXEXT optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
error occured: Failed to init sdl with joystick. Exiting...
[wounded:~] 
```

What is happening x.x

---

### Post by Dragonslicer on 2007-10-09
I'm getting the same errors (Kubuntu 7.04). I was kinda hoping to be able to use my gamepad for some of these games that don't support it directly.

---

