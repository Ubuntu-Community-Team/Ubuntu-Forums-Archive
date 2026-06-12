---
title: "Is it possible to change the refresh rate?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Jimpdx on 2007-03-10
Greetings all!  My install of 6.10 set the refresh rate at 76 Hz, and this value seems to be locked in.  I've added the line in the "Monitor" section in xorg to keep the vertical RR in the specified range (56-75), but to no avail.  My display adapter is an SiS 760GX, for which there is no Linux driver, so I am using the default driver.  What I want to do is set the RR at 60 Hz, which, in my experience, is the best choice for the resolution that I'm using.  Is there a way to set the refresh rate without buying a video card that offers Linux support?

---

### Post by oilchangeguy on 2007-03-10
the refresh rates seem to be different in ubuntu, as compaired to what windows uses. i'm using 6.06 and the max refresh rate is 60hz. and i'm using a crt monitor not an lcd. if i were running windows i'd probably use 75-85hz. as long as the monitor is not flickering, let ubuntu do it's thing.

---

### Post by ZeroWing on 2007-03-10
I've been wondering this, as well. I've managed to get a custom resolution, but that's all.

---

### Post by Patrick K on 2007-03-10
Higher refresh rate are much better for your eyes. 60hz is very low and in all likelihood you will see flicker. 75hz is consider pretty much the minimum for comfortable viewing. Low RR, like 60hz, can be very tiring. 

Also, I don't think the Gnome desktop reads refresh rates correctly. The "Screen Resolution Preferences" applet on my system says the refresh rate is 50hz. Running the command "nvidia-settings -q all | grep RefreshRate", which probably won't work for your card, says the refresh rate is actually 85hz. There is no flicker so I think it is correct. In addition the gnome applet only offers 50, 54, 55 as options.

---

### Post by IYY on 2007-03-10
I don't really understand why you would want a lower refresh rate if your resolution allows a higher one. Of course, if you *insist*, here's how you do it:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

