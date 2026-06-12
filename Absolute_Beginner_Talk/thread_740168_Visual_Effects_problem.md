---
title: "Visual Effects problem"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-03-30
Two days b4 i install emerald theme manager, and tried to change themes.it is working fine.But for this i have to enable Visual effects.
So i change it form none to normal.But after some time my pc went to logon screen without showing any error.When i switch back to none,its ok.if normal or extra.it went to logon screen after random time.Dunno wat problem is this.
Any help,how could i solve this...

---

### Post by smurphy_it on 2008-03-30
1st.  What kind of a video card is this you are talking about ?
2nd  What is the output of this command when you run it in a terminal ?

sudo glxinfo | grep direct

It should state that direct rendering is either yes or no.

---

### Post by mmarif4u on 2008-03-31
1st-Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller

2nd-
> arif@ANL-Laptop:~$ sudo glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


---

### Post by smurphy_it on 2008-03-31
in a terminal type sudo apt-get install 915resolution that is a package for the intel 945G chipset.

If that doesn't work, perhaps an updated intel video driver will do the trick.

---

### Post by J1m on 2008-03-31
If you go through the menus and find where you can change your graphics card driver (can't remember which menu entry it is) there is an "Experimental Intel" driver, or something similar.  I had to manually specify this driver on my old eMachines laptop to get Visual Effects working.

I don't know why, but a couple of times this driver would change to something else on its own, I think when I was trying to use a secondary display, so I would have to go back through the menus and re-select this intel experimental driver.

Hope that helps

---

