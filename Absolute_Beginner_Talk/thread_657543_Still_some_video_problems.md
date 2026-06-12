---
title: "Still some video problems"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by kevmore on 2008-01-03
OK I still have some small problems.  First of all I got ati's new display driver, and installed it.  Now I have an ATI Catalyst Control Center in accessories but I can't get the screen into 1680 X 1050.  I don't even have a spot for desktop effects( like fiesty), and the tv out is all messed up, no matter what settings I use.  Also I get a blank screen until I enter my username and password, then my desktop shows up....sometimes.  Other than those small things it works great.  I can play any type of video, and music works as well.  I am getting better at the terminal and can even install a few things.

I've read a lot of the posts but I can't seem to find the one that is going to help me.

---

### Post by JRanch on 2008-01-24
ATI has just released a new version 8.1 of the proprietary driver which is supposed to fix one of the 1680x1050 mode issues, but they are still recognizing another issue with that screen resolution.  Per ATI's 8.1 release notes:

> 
Resolved Issues: 
Connecting a display device that supports 1680x1050 to a system running Linux will no longer result in a maximum display resolution of 1280x1024 only being available
...

Known Issues: 
On workstation hardware 3D applications will be corrupted if the screen width is not an integer multiple of 64 pixels, for example with a 1680x1050 wide screen display. Further details can be found in topic number 737-31720
...


For desktop effects try installing the package "gnome-compiz-manager" a new menu item will appear under system, which should allow you to set everything up the way you would like it.

Can you be more specific how the "tv out is all messed up?" Are you getting anything on the display, does it even slightly resemble your desktop, is it blank, random lines and colors?

For the blank screen issue, try switching the display output to: DVI from head 1, DVI from head 2, VGA from head 1, VGA from head 2.  Sometimes only one/some of them will work correctly.

---

### Post by kevmore on 2008-02-03
Hi JRanch

The tv out is there, it's just messed up like the resolution is wrong.  It looks like my win xp when it boots up it's all skewed, but when win xp actually starts it is right.

---

