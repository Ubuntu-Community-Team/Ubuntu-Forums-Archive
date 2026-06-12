---
title: "video problems"
date: 2004-11-07
forum: Apple PPC Users
---

### Post by trash on 2004-11-07
Hi all,

Well so far I am impressed, the install and partitioning went really smoothly on my g4, 466. 

I tried my old video setting that worked for Yellowdog but it's not working in Ubuntu, can anybody help me with this?
The old setting was..

video=aty128fb:vmode:13,cmode:16 3

my screen res is a max 600x800(it's an old apple monitor)

thanks

---

### Post by Viro on 2004-11-07
[QUOTE=trash]Hi all,

Well so far I am impressed, the install and partitioning went really smoothly on my g4, 466. 

I tried my old video setting that worked for Yellowdog but it's not working in Ubuntu, can anybody help me with this?
The old setting was..

video=aty128fb:vmode:13,cmode:16 3

my screen res is a max 600x800(it's an old apple monitor)

thanks[/QUOTE]
 What video setting is this? UbuntuLinux should automatically detect what setting to run X11 in. Or are you talking about the kernel framebuffer?

---

### Post by trash on 2004-11-07
Hey Viro,
I had the same problem with Yellowdog, for some reason the installer should but wouldn't detect the right device. Basically once I boot up I get a scrolling screen
My video card is
ATI, Rage 128pro

What I do is at the first boot prompt I hit 'l', at the second boot prompt i enter "Linux video=aty128fb"vmode:13,cmode:16 3" this allows me to read the boot process however once the graphical/ desktop or login screen comes up, the screen starts scrolling... refresh rate? If i just hit enter(without 'video=...' i connot even read the boot process, it scrols the same way the graphical does.
hope this helps a bit.

thanks

---

### Post by trash on 2004-11-07
Ok, it was just the H/V refresh rates that needed changing... check for your monitor here...

[http://www.monitorworld.com/Monitors](http://www.monitorworld.com/Monitors)

---

