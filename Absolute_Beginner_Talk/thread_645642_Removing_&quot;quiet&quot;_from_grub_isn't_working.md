---
title: "Removing &quot;quiet&quot; from grub isn't working"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Cruisercommander on 2007-12-20
When I use "esc" to enter the grub setup mode, I edit the grub with "e" and  delete the "quiet" line with "d" then boot by hitting "b".  I still have a blank screen until it boots (5 minutes later).  I'm still trying to find out where my presario 1500 is hanging-up.  Any suggestions?

---

### Post by chippy99 on 2007-12-20
try taking out the splash command as well. I had this on 64 bit version and splash screen was not working.

---

### Post by philinux on 2007-12-20
See the link below for known workarounds.

You can also install from synaptic startupmanager. Options include see messages.

---

### Post by staticvoid on 2007-12-20
Try adding vga=791

Sv

---

