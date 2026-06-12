---
title: "No direct rendering after using Envy"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-10-28
I installed Ubuntu yesterday.  The open-source driver for my card immediately freezes my system before I can even log in, so I switched to the restricted driver, fglrx.  It doesn't crash my system for normal use, at least it hasn't yet.  Well, I tried to run Open Arena but it froze, and I'm pretty sure it is a driver problem simply because I've had driver problems ever since I've been working with Ubuntu on LiveCDs.

Since the driver in the repos is 8.37 IIRC, I decided to use Envy to get 8.40 in hopes that it might fix the freezing problems with Open Arena (and I would assume other 3D games.)  I disabled the restricted driver in the RDM, rebooted the machine (which was then running VESA) and then I ran Envy.  It installed the 8.40 driver, or so I thought.  I restarted like it asked me to but when I rebooted I did glxinfo | grep direct and got this error message:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


So I guess the driver wasn't installed properly or something.  Any idea what I should do?  

While typing this post I checked what the latest driver available was and it looks like they finally updated to 8.42 on the website.  Should I uninstall the driver Envy installed and try to get 8.42 or is it still bug ridden and worthless?  If I SHOULD get 8.42, how do I go about installing it?  I've never installed a driver manually on Linux before.

edit:  I used Envy to uninstall the Ati driver that it installed, then I reenabled the restricted driver through the RDM.  I'm still getting that same error message aka no direct rendering.  Can someone help?

---

