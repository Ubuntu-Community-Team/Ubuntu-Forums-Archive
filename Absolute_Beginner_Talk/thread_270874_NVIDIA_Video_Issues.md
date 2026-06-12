---
title: "NVIDIA Video Issues"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by misfit815 on 2006-10-03
I have an NVIDIA nForce2 mainboard.  According to NVIDIA, all of the drivers I'd need should be tucked away somewhere within Dapper Drake.

When I originally installed the OS, it didn't recognize anything over 640x480.  Through some desperate searching, I found a set of commands that essentially restarted the peripheral discovery process in the terminal.  I was able to manually specify 1024x768 within there, and life was good.  Of course, the smart thing to do would be to write down what I ran, or at least where I got it... oh well.

So, now that I'm getting deeper into things, I've realized that OpenGL isn't exactly working yet.  I figured this had something to do with my hacked device driver configuration, so I poked around and found the Device Manager.  And here's what I found:

- nForce2 AGP (different version?)
- nForce2 AGP
--- NV18 [GeForce 4 MX - nForce GPU]

That just didn't look right.  The problem is that I'm not sure what the current state of things is, and not sure what to do next.  By the way, I'm guessing that OpenGL doesn't work because of the following message I got in Wine while trying out a game:

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!

...and so on (btw, somebody spelled Initialization wrong).

Any help out there on figuring out where I'm at and where I'm going?

Thanks.

J

---

### Post by Imsati on 2006-10-03
Yeah, my NVidia was simply disgusting to install correctly. There are two sets of repositories though, Legascy and something else. Have you tried installing the one other than what you currently have and see if that clears it up?

"(btw, somebody spelled Initialization wrong)." - Cute, and kudos for spelling--good eyes! You win...THE PRIZE!!!

---

### Post by bodhi.zazen on 2006-10-03
Try this thread:

[Ubuntu NVIDIA nForce2](http://ubuntuforums.org/archive/index.php/t-21541.html)

---

