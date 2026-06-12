---
title: "MPlayer problem: init error in ioctl"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by shoagun on 2006-07-30
This is my first time using linux on a home computer.  I installed Ubuntu 6.06 LTS on my Dell Latitude D810 (which has an ATI Radeon x600 graphics card).  Everything worked really well, and I even got Xgl+Compiz running smoothly. 

However, I can't get MPlayer to work.  I get sound but no video.  I have found many instances of this problem, but none of the solutions seem to work.  I have tried installing MPlayer from package, using Automatix, and from source.  I always get the same problem.  When I run it on the command line, I get:

Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
93 audio & 211 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".


I have not tried editing system startup scripts because:
1.  I don't know whcih script I am supposed to edit
2.  I am not sure what max-user-freq is used for, so I'm reluctant to do something that will change it at start up.  Normally, it is a file with just the line:

60


Anyway, if anyone has any suggestions, they'd be appreciated.

p.s. This is my firt post here, so if I'm in the wrong place, please redirect me.  Thanks.

---

### Post by nalmeth on 2006-07-30
That's pretty impressive how fast you've caught on to things!

Right click the video window or the control panel, and go into preferences. 
Try changing the video driver from whatever it is now.

X11 or XV

---

### Post by shoagun on 2006-07-30
Thanks for the suggestion.  I looked, and alreayd had that driver.  However, in the process of playing with it, I figured out the problem.  I'm embarassed to say that video has been playing all along.  Only... it was showing up on a different desktop, mostly off the screen.

It looks like my only gripe with Ubuntu is solved, and I'm happy to finally be on a linux desktop.

---

