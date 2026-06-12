---
title: "Clock always wrong after restart."
date: 2007-06-19
forum: Apple PPC Users
---

### Post by magnolia fan on 2007-06-19
Hi,
I can't seem to get the Time to stay accurate after restarts.  I can sync the Time and Date and the clock updates to show the correct time, but it always reverts to an inaccurate time following a restart.  Any ideas?  My system specs are in the sig.  --THANKS

---

### Post by pxwpxw on 2007-06-20
My g4 and g5 run macosx and use UTC in the local open firmware hardware clock, not local time.  You may have configured for local time (when configuring time-zone/clock durig install). Causes silly times after  restart, also upsets macosx. 
You can reconfigure using dpkg-reconfigure  (some package I forget) or in startup scripts. 

# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
**UTC=yes**
VERBOSE=no
FSCKFIX=no

Or that may not be your problem.

---

### Post by magnolia fan on 2007-06-20
Problem solved, hurray!  It was a UTC problem, but not exactly what we thought.  My /etc/default/rcS settings matched those recommended by PXWPXW so there was nothing to change.  I ended up having to change the Date and Time Preferences using the GUI by right-clicking on the Date and Time displayed in my top menu bar.  It was there that it was set to Local time.  I changed it to UTC and everything is fine after restarts now.  --THANKS

---

