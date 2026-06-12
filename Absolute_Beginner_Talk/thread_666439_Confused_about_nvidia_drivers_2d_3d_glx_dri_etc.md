---
title: "Confused about nvidia drivers: 2d 3d glx dri etc"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Elle Stone on 2008-01-13
Hi, all,

I'm confused about nvidia driver options. I have the Gutsy restricted nvidia driver installed and it's working just fine.  I'd just like to know a little more about whether I really need this driver.

I don't do anything 3d, at least I think I don't.  Is photo-editing a 2d thing?  

What does "glx" and "dri" and "opengl" actually mean?  How do you know if you need it/them?  

Is Nouveau ready for prime-time?  Is it also only for the "glx dri opengl" stuff, whatever that is?

Is "3d vs 2d" the only limitation of the "nv" driver?  What about power conservaton?  When I start my computer my graphics card fan spins at full speed.  But as soon as I use "startx" to start my icewm desktop, my graphics card fan stops spinning at full speed.  Is the restricted driver necessary to control fan speed?  Also, I have two monitors and nvidia twinview is working just fine.  Is dual-monitor possible without the restricted driver?  

Is there anything else that the restricted driver does, that nv doesn't do, other than 3d?  Or am I so confused about the various driver options that my questions don't even make sense?

Thanks for any insight.

Elle

---

### Post by kyphi on 2008-01-13
glx is an interface between OpenGL, a computer programming language and X which is your Linux windows system - and I would recommend that you have it enabled.

If everything is working to your satisfaction then it is better to leave your settings as they are.

---

### Post by nikoPSK on 2008-01-13
GLX is what most users have. :)

---

### Post by Elle Stone on 2008-01-14
Hmm, well, generally I do believe "if it ain't broke don't fix it".  However, I'm still curious whether anything I do on my computer actually uses glx or anything else provided by the nvidia driver: raw converters? cinepaint? the gimp? photoshop (under wine or virtualbox)?  

Also, I see the latest nvidia driver from nvidia is dated Dec 20, 2007, which is after Gutsy was released.  Is the restricted driver in Gutsy the same as the nvidia driver?  Is the Gutsy restricted driver kept in lock-step with the nvidia driver from the nvidia website?  The latest nvidia release says, among other improvements, that it:

#Fixed several X rendering issues
# Improved usability of NVIDIA-settings at lower resolutions like 1024x768 and 800x600.
# Improved GLX visual consolidation when using Xinerama with Quadro/GeForce 8 series and older GPUs.
# Added experimental support for running the X server at Depth 30 (10 bits per component) on Quadro G8x and later GPUs.
# Worked around a Linux kernel/toolchain bug that caused soft lockup errors when suspending on some Intel systems.

So all the above sounds like the nvidia driver does do more than just provide glx (I have a geforce 7 card).  And some of the upgrades sound useful - I usually have my monitor set at 1024x768.  So what exactly is the relationship between the gutsy restricted nvidia driver and the "real" nvidia driver?  Now that I have the restricted driver installed, is there any way to intall/upgrade to the latest nvidia driver?

[http://en.wikipedia.org/wiki/OpenGL](http://en.wikipedia.org/wiki/OpenGL) give interesting general information about opengl, and mentions "Mesa 3D – An open source implementation of OpenGL".  I guess the name "opengl" is a bit misleading, it's not open-source, apparently.  I'm not an open-source purist - I'm just curious and puzzled.  

Elle

---

