---
title: "flashing keyboard and frozen mouse"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by RedViking on 2007-09-17
I stepped away from my Ubuntu desktop for a moment to check something on my laptop, and when I returned the mouse was unresponsive.  The keyboard lights are flashing (at least the caps lock and scroll lock are...num lock isn't) and the keyboard also appears frozen.  

Also of note, the screen usually goes into save mode after a few minutes and it hasn't done that...Any suggestions?

---

### Post by nonewmsgs on 2007-09-17
that might be a kernal panic or a lock and im not sure which.

if you have 2 kernals in your grub menu try picking the other one and see if that helps.  

does this happen a  lot or is this a one time thing?

---

### Post by DM was on fire! on 2007-09-17
Sounds like a kernel panic to me. 
Restart it and run recovery mode.

---

### Post by asmoore82 on 2007-09-17
you are definitely describing a kernel panic;
when this happens you should try to restart the system somewhat gracefully
by holding down Alt and SysRq(Print Screen) and typing the letters e, s, b
This tells the Linux Kernel to
t**E**rminate all processes,
**S**ync the disks,
and re**B**oot the machine.

the computer should restart within seconds of the Alt+Sysrq+B combo;
if it does not, the problem is more likely to be caused by some malfunctioning hardware/driver.

other causes of this could be:
overheating CPU or Video Card, bad RAM,
or trying to start a 3D screensaver without 3D hardware support.

---

