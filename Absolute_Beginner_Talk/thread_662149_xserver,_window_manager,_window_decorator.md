---
title: "xserver, window manager, window decorator"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by blueridgedog on 2008-01-08
OK, I could use some *big picture advice* on the relationship and configuration methods for each of the following.

**Xservers:**
I have run xorg server and xserver-xgl, but never understood how to switch back and forth manually other than installing/uninstalling xserver-xgl.  Also, when running xserver-xgl I noticed that xorg was also running.  How would I select one versus the other.
[B]
Window Manager:[/B]
I have two window managers installed, metacity and compiz.  Are there more?  How do I set the default window manager (what config file, assume I want to set it from the terminal)?  I understand how to change to a given window manager (compiz --replace) but I don't know how to pick a starting one.

**Window Decorator:**
What is this and how is it related to the window manger?  I have two installed (emerald and GTK) but without the Compiz Fusion Icon, I can't imagine how to switch between the two or how to configure one or the other from the terminal.  Also, are there any others?

And finally, I would like a generalized "here is how these three things interrelate" lesson (webside, wikki, etc).  I am not interested in "fixing a problem" per say, but I am interested in understanding how these tools start, stop, are configured, upgraded and monitored.

I have run linux servers for a long time, but I am now to the desktop and really want to understand it as well as I understand the rest of the system.

---

### Post by Hospadar on 2008-01-08
Hullo

This can be a confusing area, it took me a while and several attempts to install beryl on 7.04 to really understand it.

xservers:
this is the lowest level of your graphical interface.  every window you have on your screen, is basically a software object in your xserver.  I'm not entirely sure what the difference between xorg and xgl, but I believe that xorg provides non-3d graphics in an open source fashion (i.e. without proprietary drivers from vendors) where as xgl provides open-source 3d and in general allows opengl (glx) to be used without proprietary drivers (albeit with less performance that proprietary drivers))

The window manager handles moving windows, window titlebars close buttons and the like.  there are other window managers, for example fluxbox or joe's window manager (which are lightweight WM's used by distro's like puppy and dsl)  you can install and change to these.  And i'm not sure, but I think running a command like "compiz --replace" will make compiz the default window manager (I could be wrong)

Window decorators are used by managers to draw specific themes and borders onto the windows.  you can change these from the command line much like changing a window manager.  try doing a "nohup emerald --replace" or "nohup metacity --replace" (nohup so your borders don't disappear  when you close the terminal, it wouldn't be needed if it was in a startup script or a launcher)

As for general information, I know there are good sites for stuff like basic CLI, so I'd assume similar information exists for other aspects, but you might want to look towards books for info on more complex stuff like window management, since the average user will probably never really bother with manual replacement and installation.

Also:
As a general disclaimer, I'm sure i'm not *exactly* right on some of this, so if someone else knows better, please correct be, I'd be very interested to hear it.

---

### Post by blueridgedog on 2008-01-08
Thanks...I like "knowing" what is happening and how the parts fit together.

---

### Post by shareMenaPeace on 2008-01-08
im not very sure but you might want to install with synaptic

compizconfig-settings-manager

just search for compizconfig and install this manager for compiz settings.
 
For window decortations search synaptic for emerald and isntall this window decoratour.

Sorry if this is not required but i thought i throw in a few ideas.

Cheers:popcorn:

---

### Post by blueridgedog on 2008-01-08
Thanks.  I have the manager installed and have played with it a bit, the end result is that I probably can live without it.  

I am not certain if it was the window manger (compiz) or the window decorator (emerald), but for some odd reason the combination makes paging in firefox or any other gui vaguely "frame like".  

I may try metacity/emerald together and see if that changes things or for that mater compiz/GTK.

---

