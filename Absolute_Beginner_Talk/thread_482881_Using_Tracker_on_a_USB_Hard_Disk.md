---
title: "Using Tracker on a USB Hard Disk"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Babu_Shenoy on 2007-06-24
I have downloaded Tracker using the Add/Remove tool
I'm not able however to use Tracker on my USB external Hard Disk... which is the place where I keep all my data!
What should I do?

:(

---

### Post by Franko30 on 2007-07-10
Hi,

to include this harddisc, do the following:

    * end/kill tracked (for instance via gnome-system-monitor)
    * go to /home/yourdirectory/.Tracker
    * in the .Tracker directory, edit the tracker,cfg file to be sure all the directories and mountpoints you want to be indexed have an entry in this file
    * restart tracker manually ba typing trackerd in a terminal
    * to see even more of what's going on, use the trackerd --verbosity=1 option
    * check, if trackerd is part of the automatic startup programs in System->Settings->Sessions, so that it starts up automatically after the next reboot

Cheers

Franko30

---

