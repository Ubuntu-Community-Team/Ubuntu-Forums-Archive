---
title: "ubuntu7.10 very slow"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by cookiemonster0774 on 2007-12-26
Merry christmas everyone;

I have recently installed ubuntu to my laptop (that was a chore no cdrom and no linux experience) but I got it on and had it working. I installed ubuntu 6.10 and was very pleased with the boost it gave to my laptop. It's practically a windup toy. I then upgraded to ubuntu 7.04 again great then 7.10 and again my laptop is moving slower than moss. Any advice on what to look for to fix this problem would be great you guys have saved my but in the past and I know this will be a no brainer for you.

thanx

---

### Post by jonmartin on 2007-12-26
Use top to see if you have any background processes running. Maybe some document indexing service. Have you installed any accellerated driver for your videocard? Open the appearance applet in preferences menu and turn off eyecandy. Latest desktop versions of linux have lots of 3d stuff that might take up resources for you. Check if you can disable any services/daemons.

---

### Post by cookiemonster0774 on 2007-12-26
Is there that much of a difference between 7.04 and 7.10. It doesn't seem to have any of the "eye candy" turned on. The only reason I up graded is for gtk-gnutella are there any alternatives that will run on older versions. In processes system monitor was using 71% of the cpu.

---

### Post by funrider on 2007-12-26
you can speed up the box by disabling visual effect.

System > Preferences > Appearance > Visual Effect Tabs

---

### Post by eolson on 2007-12-26
> In processes system monitor was using 71% of the cpu.

I don't know what the fix is,   but that's very well your problem.  mine only shows about 2 percent.

---

### Post by cookiemonster0774 on 2007-12-26
just the process "system monitor" was 71% can I do this from command line.

---

### Post by Clickbg on 2007-12-26
Switch to console mode, that means no GUI - Gnome or KDE and write uptime. You will see three numbers like those load average: 0.52, 0.63, 0.93 if they are still upper than 1 your problem is from hardware type. It is quite often with laptops to become slower when they are too hot.

---

### Post by Josh1 on 2007-12-26
If it's an old laptop, try XUbuntu instead.. it's very light weight.

---

### Post by cookiemonster0774 on 2007-12-26
> **Josh1 said:**
> If it's an old laptop, try XUbuntu instead.. it's very light weight.

will gtk-gnutellla still work on xubuntu

---

