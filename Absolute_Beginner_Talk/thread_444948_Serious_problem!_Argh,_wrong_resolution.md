---
title: "Serious problem! Argh, wrong resolution"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-05-15
Okay, I desperately needed to install graphics drivers for my Ubuntu (6.06)  partition, so I used a little script called Envy to do that automatically for me.

All seemed fine when installing, but when it restarted, it came to light that Ubuntu was trying to boot into 1600 x 1200 (or something like that) and my monitor only supports 1024x768,  so it just says "out of range".

This is a problem, because now I can't boot.

HOWEVER, I can get into the command line.

So, could some helpful fellow tell me, line by line, exactly what I need to type to set the default resolution to 1024x768?

I presume it's something to do with the xorg.conf file, but I don't really want to be messing around with that because it could easily go wrong.


so please, can somebody help me!?

I appreciate any help you can give.

---

### Post by Neon_Knight on 2007-05-15
okay, I sorted it out using the 
```

reconfigure xserver-xorg

```
command ( or something like that), but now I've lost all hrdware acceleration...any way of solving this?

---

### Post by linuksman on 2007-05-15
I'm having a similar problem, I think. I can boot from the Live CD, and install via the icon on the desktop, but afterwards, it takes forever to startup, and finally gave me an overscan, or overrange, notification on my monitor.  After restarting and removing some of my USB devices, and waiting for 20 min, it finally came up with a screen and then it looks like it's starting to load and I get a thinking mouse icon, and it seems to freeze up here.  I can move the mouse but it updates the mouse position very slowly (as if there were no gfx driver).

I have an ATI x800 pro , 3500+ athlon 64, ECS NFORCE4-A939, Scepter NAGA 22", etc. any help is appreciated. ty

---

### Post by zvacet on 2007-05-15
**ctrl+alt+F1**

```
sudo dpkg-reconfigure xserver-xorg
```

select **vesa** and after that go and find proper drivers for your card

---

