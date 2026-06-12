---
title: "Can't start Ubuntu due to Beryl in Startup"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Latish on 2006-11-28
I'm in a real bind here.  I accidentally put Beryl in my startup folder (usually NOT a bad thing...).  However, whenever I start Beryl, it crashes and I log out of Ubuntu.

The result is that I cannot log in now.  If I try to log in, Beryl immediately starts since it is in startup and thus crashes and I log out.

I have tried logging in to different sessions and the only one that is stable is the command line one.  However, I don't know how to remove a program from start up using command line - or how to fix my Beryl so that it works (whichever is easier).

Any help here?  I'm forced to use Windows in the meantime? :(

---

### Post by ThePod on 2006-11-29
I'm having a similar problem.  Beryl 0.1.2 was stable (ish) for me and I could use it. 0.1.3 is hanging up X.

I've used 


sudo apt-get remove beryl

from the command line.

See if that works for you

---

### Post by KatanaSwordfish on 2006-11-29
Im definately no pro! but;

could you boot off of a Ubuntu Live-CD and uninstall/reinstall beryl that way?

don't know if that would work for you, just throwing the idea out.

---

