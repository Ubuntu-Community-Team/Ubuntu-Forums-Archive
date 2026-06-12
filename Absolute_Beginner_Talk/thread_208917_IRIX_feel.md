---
title: "IRIX feel"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by jonnymorris on 2006-07-04
Hi!

I'm coming from an IRIX background, have got a G4 Cube with dual-boot linux partition and OSX partition; at the moment it has Yellow Dog on the linux partition but I've found this to be too slow, I tried the Ubuntu LiveCD and it seems a lot quicker but it still has that nasty Windows feel to it - the task bar, the Start Menu at the top, etc.  I don't mind a Start Menu but really don't want the whole bar across the top of the screen (would much prefer it to look like the IRIX Tool Chest!), can that be easily customized?  Can I completely remove the bottom bar too?  I would much rather have apps minimize to an icon on the desktop than to a task bar, like they do in IRIX.  I have IRIX on my SGI machines but thought it would be nice to have a version of linux in my toolbox too :)  I really hate Windows btw, in case you hadn't gathered by now ;)  Also while I'm about it I don't like the default Ubuntu window decorations (wrt minimize, maximize, close buttons), can these be customized too?

I have been made aware of Xubuntu, however it still appears to have those annoying task bars etc.  Is there a guide for doing all this sort of thing?  I'm no stranger to the shell.

All help and advice is much appreciated!

---

### Post by mcduck on 2006-07-04
All things in panels can be configured, and you can have any amount of panels you want. Also the panels can be set to not expand to whole screen. Altough Gnome doesn't have any way to use only icons in taskbar (you can do this in XFCE, and it has pretty much as configurable panels as Gnome does)

To start, right-click on your panel and you'll get a nice popup menu where you can do several things:

Select 'Properties' to configure the panel autohiding, expanding, size, color and transparency

Select 'Add to Panel' to get a window with lots of cool applets you can put to your panel.

And then there's options to remove the panel, or add a new panel.

You can move your panels around simply by dragging them where you want.

All items in panels are movable, you can either drag them around with middle mouse button, or right-click and select 'move'. Note that items can also be locked by right-clicking and selecting 'Lock to panel', so if something refuses to move make sure it isn't locked.

I only have very faint idea what IRIX looks like (does it use CDE?), so if you want to stick to Gnome you may not get it to look *exactly* like IRIX, but I hope this helps you to make Gnome feel more like home to you ;)

Also, there are many more window managers available, perhaps one of them would be even closer to IRIX than what you can get with Gnome.. Take a look at FVWM, for example.

---

### Post by Ptero-4 on 2007-12-04
If you want the IRIX look, you might be interested in xubuntu. The desktop handler (xfdesktop) allows you to minimize apps to the desktop. Also you can get motif-like themes (motif is the design type used by CDE and also by IRIX) for xfwm4 (the xfce wm) and you can move the titlebar buttons around, you can remove one panel and move the other to the side and remove the taskbar and add applets (just use the right click menu in the panel to do your stuff), also xfdesktop puts the start menu as the desktop right click menu so you can get rid of the start button in the panel.

---

