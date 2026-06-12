---
title: "Desktop CD can't run the OS"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Kossilar on 2007-01-06
Hello,

I've been thinking about making the change from Windows to Linux, and downloaded the Ubuntu 6.1 disk to try it out. Unfortunately, the OS failed to load and gave me nothing but green lines on the screen.

I tried setting various resolutions to see if it was a graphical issue and several times I got images of the OS, only distorted, like when you set your system to display a resolution that it can't handle. 

Not sure what I can do to get this working, I'm hesitant to install the OS before I get a look at it and make sure it can handle my hardware.

I'm running an Intel dualcore 2.8 processor, 2gb ram and Geforce 6800GS.

Any help that can be offered is much appreciated.

Thanks.

---

### Post by steve.horsley on 2007-01-06
It could be that your monitor can't handle the resolution that the video driver is choosing. Try this:
Press Ctrl-Alt-F2 to get a text-mode prompt. 
Enter the command **sudo dpkg-reconfigure xserver-xorg**
Take the defaults except when it asks about the screen resolutions you want.
When you have finished, use the command **sudo /etc/init.d/gdm restart**

G'luck

---

### Post by thinklife on 2007-01-06
The burning might be wrong. Try burning the iso at lower speed of 4x and then boot from the cd. That might work. :cool:

---

### Post by Kossilar on 2007-01-06
> **steve.horsley said:**
> It could be that your monitor can't handle the resolution that the video driver is choosing. Try this:
Press Ctrl-Alt-F2 to get a text-mode prompt. 
Enter the command **sudo dpkg-reconfigure xserver-xorg**
Take the defaults except when it asks about the screen resolutions you want.
When you have finished, use the command **sudo /etc/init.d/gdm restart**

G'luck

Okay I did what you said, after typing in the last command, the system returned the following:

* Stopping GNOME Display Manager...      [ ok ]
* Starting GNOME Display Manager...      [fail]

Nothing else happened. I'm going to try running the commands again, then I'll swap out my monitor for a different one and see if that helps.

---

### Post by Kossilar on 2007-01-06
Sorry, it seems my previous post was premature. I rebooted the system, set the res to 1024/768 and it booted fine. Only problem is that now the mouse pointer doesn't show up.

I can still move the mouse and interact with the OS, but I can't see the actual pointer.

Interesting coincidence since I have the same problem with the Windows XP installation on this system, but I solve the problem by turning on mouse trails :P

I wonder if its a problem with my monitor or video card...

The monitor on the system I'm talking about is a ViewSonic P810 19 inch.

Thanks for all your help guys. I really appreciate it.

---

