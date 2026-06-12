---
title: "I seem to be getting logged out from the desktop"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by bodam on 2007-05-03
I am a new Linux user and I have 7.04 installed.   When I walk away from the system for a period of time, my session seems to be terminated and I have to log in again, losing any unsaved work.  Upon looking at the logs I see the following two suspicious entries:

GConf server is not in use, shutting down
Exiting

Any suggestions?

Dave

---

### Post by ubnewbie2 on 2007-05-03
hmmm, I noticed once or twice that a screensaver would upset (crash/restart) Xwindows.  This will land you back at the login prompt just as if you had pressed ctrl-alt-backspace.  This might be what is happening.  Try turning off the screensaver to test it.

---

### Post by ckoester on 2007-05-05
I'm having the same problem.  It started happening after I tried changing the screensaver.  Now If I attempt to change the screensaver settings it abruptly crashes X.

I tried reinstalling gnome-screensaver and it is still crashing.  Will have to try manually changing screensaver unless anyone has any better ideas....

---

