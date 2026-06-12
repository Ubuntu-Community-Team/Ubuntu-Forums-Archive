---
title: "how do i enable the mouse"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by lreyes6 on 2005-12-20
i need to enable use the mose on an ubuntu box installed as a server (no desktop manager) 

thanks for the help

---

### Post by PilotEd on 2005-12-20
[QUOTE=lreyes6]i need to enable use the mose on an ubuntu box installed as a server (no desktop manager) 

thanks for the help[/QUOTE]

I had the same problem.  Here's a solution:

Modify the /etc/modules file and add proto=bare to the psmouse line. My modified /etc/modules file is shown below:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with '#" are ignored.

lp
mousedev
psmouse proto=bare


------
Source:
[http://www.redhat.com/archives/fedor.../msg00717.html](http://www.redhat.com/archives/fedor.../msg00717.html)

---

