---
title: "openoffice will not boot"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Waldo22 on 2007-10-07
I downloaded the OpenOffice upgrades, and it initially booted fine, but after a shutdown and restart, it won't boot to any of the applications.  The splash screen comes up momentarily, then just disappears.  Any suggestions?  I am brand new, by the way.

---

### Post by randcoop on 2007-10-07
Could be any number of things.  One of the best ways to diagnose a problem is to try starting a program from the command line.  When there are problems, the errors are reported in the terminal and you can figure out what went wrong.  

Since you indicated that you "upgraded" OpenOffice, it may be installed to a different directory.  The new openoffice (2.3) installs by default to /opt.  If your menu command is to run oofice, then you won't get OpenOffice2.3 to start.

For starters, determine what your menu command is.  Then try running that command in a terminal in order to see the errors.

If that doesn't work, see if OpenOffice 2.3 is installed in /opt/openoffice.org2.3.  If it is, then try running:

/opt/openoffice.org2.3/program/soffice

in the terminal.

---

### Post by Irony on 2007-10-07
I assume you mean a security update not an upgrade as uprgrading doesn't happen automatically.

The update went fine for me but you might want to look in the search function as a number of people have had problems, e.g.;

[http://ubuntuforums.org/showthread.php?t=567803&highlight=openoffice+update](http://ubuntuforums.org/showthread.php?t=567803&highlight=openoffice+update)

---

### Post by Waldo22 on 2007-10-08
I think I have my own solution: I will wait until Ubuntu 7.1 comes out, and then reinstall.  At least that should work...

---

