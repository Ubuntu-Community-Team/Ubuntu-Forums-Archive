---
title: "Getting Beryl working with Dapper AiGLX"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by evanvlane on 2006-12-12
Hey,
I'm currently going through the Install/Ubuntu/Dapper/AiGLX Beryl tutorial
at [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX) .

I've been following all the instructions thus far, and have AiGLX working and 3d acceleration enabled, but whenever I try to run beryl from the terminal all my menu bars disappear and it says:

```
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```

When going through then instruction on their wiki, the only weird part came when I tried:

```
sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r`
```

I broke it down, and the air-core and modules-common installed fine, but when i tried ```
sudo apt-get install linux-dri-modules-`uname -r`
``` the terminal came back with:



Oh, and if I start beryl-manager, it kicks me out of the GUI completely. I have to run startx from terminal to get it back.

Is there some way to get that other package? And if not, am I doing the rest of it correctly?


Thanks,

Evan.

---

### Post by Zelut on 2006-12-12
that command looks wrong to me.  Try

sudo apt-get install linux-dri-modules-$(uname -r)

---

