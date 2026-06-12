---
title: "Google Earth problems"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by SexyStud on 2007-01-26
Hello,

I tried installing Google Earth, along with other stuff, from Automatix2. I got nothing on the menu, so I installed it manually. Still, nothing. I run it from terminal, but it freezes on the Google Earth splash screen, and I get this error on terminal: 
Xlib: extension "XFree86-DRI" missing on display ":0.0".

I'm running Edgy on a P4 3.4 / 1 Gb RAM / ATI Mobility Radeon 9700

Any idea how to solve this?

---

### Post by lyceum on 2007-01-26
You can instal the Debian menu (w/ Automatix) that should show you everything. As for the program not working... sorry not sure. You may want to remove it and re-instal?

---

### Post by SexyStud on 2007-01-27
I tried reinstalling it with no success :(
I think it has something to do with my graphics card. If I run fgrlxinfo, I get the same error message of googleearth.

---

### Post by lyceum on 2007-01-27
That makes sense, I really can't think of anything else myself. Sorry. :(

---

### Post by The Union Forever on 2007-01-27
This sorta has nothing to do with SexyStuds' post but I also have a problem with Google Earth. The program loads very odd-like -- the status bar that normally is at the bottom of the screen is about halfway up on the screen...?:confused: I must keep maximizing and minimizing to reset it. Then, the right side of the map/screen lags when I zoom in, in normal use. 

I get no error messages or anything just weird stuff...

Hope this isn't too vague.

TUF

---

### Post by The Union Forever on 2007-01-27
This sorta has nothing to do with SexyStuds' post but I also have a problem with Google Earth. The program loads very odd-like -- the status bar (of the map section) that normally is at the bottom of the screen is about halfway up on the screen...?:confused: I must keep maximizing and minimizing to reset it. Then, the right side of the map/screen lags when I zoom in, in normal use. 

I get no error messages or anything just weird stuff...

Hope this isn't too vague.

TUF

---

### Post by mkoyle on 2007-01-27
> **SexyStud said:**
> Xlib: extension "XFree86-DRI" missing on display ":0.0".

I don't specifically know what the problem is exactly, but you probably want to look for information on setting up your drivers.  It is looking for 'dri' ('Direct Rendering Infrastructure').  It seems to need (or think you have installed) the optimized drivers for your ATI Mobility Radeon 9700.

My suggestion is to install the ATI drivers following the directions at [http://ubuntuforums.org/showpost.php?p=1631984&postcount=2](http://ubuntuforums.org/showpost.php?p=1631984&postcount=2) (that is an excerpt from this post that might help if you have problems [http://ubuntuforums.org/showthread.php?t=279664&highlight=ATI+mobility+radeon+9700](http://ubuntuforums.org/showthread.php?t=279664&highlight=ATI+mobility+radeon+9700) ).   If none of these help, try looking for help at [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide).

---

