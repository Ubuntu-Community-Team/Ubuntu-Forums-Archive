---
title: "Firefox no longer working"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by bigalreturns on 2007-09-06
Hi, sorry if this is in an inappropriate place, but couldn't see anywhere obvious to post it, and I'm truly an Ubuntu beginner so...

anyway, having converted to ubuntu (latest release, all updated etc.), Firefox was working perfectly.  I then downloaded several extensions, and now ff no longer starts.  I.e. when clicking the launcher, it comes up with "starting firefox", but when that disappears, there is no firefox, visible, or running as a process.  Entering "firefox" in the terminal gives the message "Segmentation fault (core dumped)".
I've tried completely removing, then reinstalling ff with the synaptic package manager, but to no avail.
Any ideas whats going on here and how to resolve it?

Thanks

---

### Post by felicity on 2007-09-06
I'm not sure what may be causing that, but you can try removing the firefox configuration folder before you reinstall. It's located in your home folder in .mozilla ( a hidden folder).

---

### Post by philinux on 2007-09-06
Also open a terminal window and type in

firefox -safe-mode

If this dosnt work reboot then try it.

---

### Post by bigalreturns on 2007-09-06
Thanks, I'll give that a try and see what happens.

edit:

Just tried starting in safe mode, and by trial and error found the extension that was causing the problem.  Working fine now thanks to you both

---

### Post by RogerFD4-Utu on 2008-04-07
Hi,
I would like to know which file extension were creating the problem.
I have the same issue. I tried to install another browser and had the same problem (it does not seem to start).

Thanks,

Roger

---

