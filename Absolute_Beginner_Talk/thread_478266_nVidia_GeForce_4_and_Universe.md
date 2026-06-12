---
title: "nVidia GeForce 4 and Universe"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by technomaniac on 2007-06-19
I have two questions
1[SIZE="4"]. I have installed nVidia Glx driver but I think its unable to detect the Graphic card. My card is GeForce 4 (64MB of Ram). My system is AthlonXP 2100+ with 512MB of Ram.
[/SIZE]
Output of glxinfo:
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Output of glxgears

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

Also I would like to know if the nvidia driver will detect the GeForce Go 7400 card on my Sony Vaio.[B][SIZE="4"]

[/B]2. How do I enable the universe component?[/SIZE]

---

### Post by renzokuken on 2007-06-19
not sure about the first part but to enable Universe run

```
gksudo gedit /etc/apt/sources.list
```

in the file that pops up, just remove the comments (i.e. the '#'s) from the start of the lines with universe in them that look something like

# deb [http://archive.ubuntu.com/edgy](http://archive.ubuntu.com/edgy) main universe      (or whatever it is)

to this 

deb [http://archive.ubuntu.com/edgy](http://archive.ubuntu.com/edgy) main universe

(just remove the #, dont change the line in any other way)

save and close the file then run

```
sudo apt-get update
```

---

