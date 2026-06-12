---
title: "Xorg high CPU usage - laggy mouse"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Lexyboy on 2007-04-02
Hi all,

For a while I've had occasional lag with the mouse in Beryl, and recently tried to fix it.  Also, X.org is using 5-40% of CPU time all the time... So, read up on the forums and seems like X.org isn't configured for my gfx card.  I tried manually reconfiguring xorg with 'sudo dpkg-reconfigure xserver-xorg' with no joy, and also tried Envy with no luck - I couldn't get any GUI at all with the automatic install (can't remember the exact error message - I think 'couldn't find device nvidia', but could have been can't find any suitable screens), but the manual install worked OK, only now the lag seems even worse!

Most of the time things are fine, but when something's happening (e.g. web page loading) the mouse & keyboard get sloooww.

So, does anyone have any suggestions?  Any help much appreciated!

My system is: Athlon64 @ 2.2GHz, nVidia GeForce 6100 256Mb, 2Gb RAM, Asus mobo.

---

### Post by Lexyboy on 2007-04-05
Think I've found part of the problem - beryl was set to AIGLX rendering (to avoid black window bug); changing to 'force nVidia' or I guess automatic avoids the laggy mouse problem, and Xorg CPU usage around 2% when doing nothing, highest it got was ~20%.  Still a bit much though, esp. as it's as high or higher with metacity, and of course with these settings I can only open 4 windows at a time :(

---

