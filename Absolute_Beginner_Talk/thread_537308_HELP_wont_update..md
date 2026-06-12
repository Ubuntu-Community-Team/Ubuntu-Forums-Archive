---
title: "HELP wont update."
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by zeehat on 2007-08-28
I have a problem..  I was playing around with settings trying to make my movie player, play .swf files.  To do this I needed to install 'restricted' packages.  Now the updater will not update neither will synaptic, or add/remove programs.  Here is the error message I get:

'Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.'

When I try to run the sudo apt-get install -f, I get a screen with some sort of agreement.  However from there I have no idea what to do.  I am really stuck.  Everything else is working from what I can tell.  I would like to reverse what I have done.  Any help is greatly appreciated.

---

### Post by zeehat on 2007-08-28
I love the critical thinking needed to solve problems in Linux. [no sarcasm intended].  When I ran this command : 'dpkg --configure -a', it appeared to fix everything.  I hope so.  Because the updater and everything would open again, without the error messages.  But I spent a good hour trying to fix the problem before I resorted to the forum.  I hope this is right.

---

