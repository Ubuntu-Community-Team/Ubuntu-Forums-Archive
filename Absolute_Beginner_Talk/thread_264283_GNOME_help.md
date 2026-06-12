---
title: "GNOME help?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by TumbiWan on 2006-09-24
ok... I'm a newbie... I have been able to add several new themes for gtk 2.x, but I cannot load new pointer themes for x11. Should I be looking for gtk2.x pointer themes?... little help? Is x11 a part of gtk2.x? And are all of them a part of gnome?

---

### Post by skymt on 2006-09-24
* X11 is the graphics system for Linux and other Unix-type systems. It's in charge of drawing all the graphics to the screen.

* GTK is a "toolkit" for X11. It's basically a bunch of widgets like buttons and text boxes. It makes programming X11 applications much easier, and makes applications much more consistent, since programmers don't all have to code their own buttons, etc.

* GNOME is a desktop environment. It's a collection of tools like the panels at the top and bottom of your screen, and the file manager used to browse and manipulate files. It also contains utilities for configuring your system, under the System menu.

To install cursors, the best way is:
* Unpack them from the .tar.gz archives they're probably in. (Open the archive and drag-and-drop the folder inside.)
* Move the folder you just unpacked to a folder called ".icons" in your home folder.

Then the new cursors will be in GNOMEs mouse preferences.

---

### Post by decoherence on 2006-09-24
That's a good question. I'm not sure how you set cursor themes from GNOME anymore.

X11/GTK/GNOME is what you'd call a 'software stack,' that is a collection of programs to accomplish a certain task like giving you a GUI, or serving website. X11 almost always forms the base of the stack and handles low end things like tracking your mouse and determining which window is in the foreground and actually throwing windows up on the screen. GTK sits on top of that and tells X11 what it's supposed to look like. GNOME sits on top of GTK and defines how it's all supposed to work together. There can be a bit of overlap, but that's basically the job of each component.

Ubuntu uses three of these stacks. X11/GTK/GNOME for regular Ubuntu, X11/GTK/XFCE for Xubuntu and X11/Qt/KDE for Kubuntu. There are also GNOME projects to create an fbdev/GTK/GNOME, which would do away with X11 and might be useful on embedded or low-resource devices.

---

### Post by TumbiWan on 2006-09-24
thanks guys.  Those comments were very helpful...

---

