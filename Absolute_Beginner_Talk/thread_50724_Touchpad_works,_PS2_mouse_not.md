---
title: "Touchpad works, PS/2 mouse not"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by tarvas on 2005-07-21
So I just installed Ubuntu and i'm new in linux, problem is that my laptop's ( Compaq Evo N1020v ) touchpad works ( thanx God :D ), but when i connect to laptop PS/2 Genius optical mouse, it doesn't work. :( Maybe somebody could help me, please?
All help is appreciated. :D

---

### Post by MrCheese on 2005-07-21
sure you've got the bios set to allow simultaneous pointing devices? Not familiar with your exact model but this is a common option on laptops.

---

### Post by tarvas on 2005-07-21
[QUOTE=MrCheese]sure you've got the bios set to allow simultaneous pointing devices? Not familiar with your exact model but this is a common option on laptops.[/QUOTE]

In Windows touchpad and PS/2 mouse worked simultaneously.

---

### Post by PilotEd on 2005-12-22
I had the same problem.  Here's what I did to get my ps/2 mouse working.

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

