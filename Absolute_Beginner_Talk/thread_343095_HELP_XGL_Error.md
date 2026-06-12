---
title: "HELP XGL Error"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by longrunner on 2007-01-20
So, I've had ubuntu for about a month, but haven't really used it much.  I had a friend who suggested I try XGL, I tried a live CD and thought it would be cool.  I found a How to on the forums and gave it a try, I figured I'd used the command lines a few times so I gave it a shot.
That was a bad idea.  I got this error.

X server not found

/usr/bin/Xgl :0 :0 -fullscreen -ac -accel
glx: pbugger -accel xv:fbo -kb
-auth/var/lib/gdm/:0.Xauth-holisten

(sorry for the space in the second line, but otherwise it gave me a smiley)

If anyone can help me either restore the gnome default, or fix Xgl I would be very appreciative.  At this point I can only boot ubuntu into command line, so there isn't very much I can do.

Thanks
longrunner

---

### Post by dbbolton on 2007-01-20
try ```
sudo dpkg-reconfigure xserver-xorg
``` from recovery mode.

---

### Post by longrunner on 2007-09-19
Is recovery mode an option on the live cd?

---

