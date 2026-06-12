---
title: "Desktop Shortcuts"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by brn on 2006-11-01
I have a couple of Windows applications I run with WINE.  I figured out a way to launch these from desktop shortcuts by first selecting a "regular" application to place there, then editing properties to change the name, icon, and command.  (I believe there is a more orthodox way to do this but haven't found it.)  This worked for the WINE applications so I tried it with a couple that were installed with Synaptic but could only run from the command line.  It acts like it's trying to execute but eventually just stops.  Gnome and KDE both do this.  I wonder 1.)  Why this trick seems to work for WINE but nothing  else, and 2.)  What would be a better way to make a shortcut for a command line launch.

---

### Post by davmac on 2006-11-01
Do you mean you want the command to run in a terminal window? If so, right click the desktop, choose add launcher and from the "type" drop down list choose "application in terminal".

This is for Egdy. I seem to remember it was similar, but not exactly the same on Dapper.

Hope this helps,

Dave Mac

---

### Post by brn on 2006-11-01
Found it!

Right-click anywhere on the desktop brings up a menu to create among other things, a new launcher.  Be sure to select "Run in Terminal" if this is appropriate.  This also explains why WINE worked in my kludge shortcuts.  They do not use the terminal.

Always overlook the obvious first. :-k

(thanks DavMac, I posted this before your reply reached me.)

---

