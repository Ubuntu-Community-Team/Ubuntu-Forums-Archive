---
title: "remote desktop client"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-31
what is the best alternative to RDP in Windows XP for Ubuntu?  i am looking for something that has the same usability, functionality and features as RDP in XP.   thanks.

---

### Post by emarkd on 2008-01-31
I don't use any of this, so consider all of this just pointers for further research.  A direction, if you will, not a solution.

Ubuntu already has something for you that may work.  Click on System > Preferences > Remote Desktop.  You should know that this is really just a front end for VNC, which is not considered very secure.  You protect the login with your password but data is passed back and forth unencrypted.  Most people get around this by what's called ssh tunnelling.  You start an ssh session and "tunnel" vnc through it.  I think TightVNC makes that easy to do and it's in Synaptic.

Another option that seems to get recommended often is [http://freenx.berlios.de/](http://freenx.berlios.de/)

---

### Post by Joeb454 on 2008-01-31
Have you tried opening Applications>Internet>Terminal Server Client ?

It has RDP support and I've used it before to connect to a Server 2003 machine with no issues.

Try that out before you start downloading anything :) It might be just what you're looking for

---

