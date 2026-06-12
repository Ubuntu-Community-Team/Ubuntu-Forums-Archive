---
title: "Screen Resolution"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Harkainos on 2007-04-18
I unlocked the 'Restricted Repositories' and downloaded the newest Nvidia-glx driver for my comp. Everything seems to work fine (graphically) except the highest resolution Ubuntu will go up to is 1152*? (or its derivative, i am at work right now). I haven't tried *sudo nvidia-config* yet, would there be any other reason why it wont allow my 19" flat panel widescreen to go to higher resolutions?

---

### Post by Terl on 2007-04-18
Hit ctrl-alt-F1 and login to the virtual terminal.  Type: sudo dpkg-reconfigure xserver-xorg  Answer the questions as they go through it.  Near the very end is the monitor info.  After you finish answering all the fields, hit ctrl-alt-f7.  It will take you back to the desktop.  Then just hit ctrl-backspace to restart the xserver.  Your new resolutions should be available now.

---

### Post by Harkainos on 2007-04-18
Wow.... that was fast. And sounds ez too.

How much do i need to know about my comp during this command process? I mean... i built it, but how much detail does it expect

---

### Post by Terl on 2007-04-18
The most important is the vertical and horizontal synch of your monitor.  You need that if you select the advanced setup (when you get to the monitor part).  You can pick the easy or one in the middle.  One asks you the resolutions you want.  Spacebar selects.

When you get to the part for your video driver, select the nvidia (not nv) and then another sections asks a list of the drivers to load (leave all selected EXCEPT dri.  just arrow down to dri and hit space to deselct).

Take the time to read the choices on each screen.  It is not bad at all.  

You probably know all you need since you built it.  Just check the monitor specs, you do not want it out of range.

---

