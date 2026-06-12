---
title: "Window Preferences: Double-click to minimize?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by OriginalGrumpyOldMan on 2007-03-17
Minor question:

In Window Preferences - Titlebar Action - Double-click to perform...
is there a way to add "Minimize" as option to make it more Mac-like?

Sorry, though I use various OS, it's just my preferred usage :tongue:

---

### Post by dbbolton on 2007-03-17
are you using Gnome or KDE ?

---

### Post by OriginalGrumpyOldMan on 2007-03-17
Default Gnome installation, otherwise I guess it'd have to be Kubuntu?

Any tips much appreciated!

---

### Post by h0ax on 2007-03-18
If I recall correctly I changed something like that in System-> Preferences -> Windows

Good Luck

---

### Post by dbbolton on 2007-03-18
i don't think it's possible to make a double-titlebar-click minimise the window. *maybe *if you toy around with gconf-editor, but i seriously doubt it, and wouldn't even know where to start.

---

### Post by OriginalGrumpyOldMan on 2007-03-18
I was afraid so.

Maybe once I've sorted out the more serious issues I keep having with my Ubuntu install, it will be fun to start digging into this subject...

---

### Post by dbbolton on 2007-03-18
there is an "OS X" preset in KDE- single-click to open folders/files, menu bar on top panel, etc.

then only mac-like implementation that i know of on Gnome is to put the titlebar buttons on the left side (gconf-editor > apps > metacity > general settings)

---

### Post by barney_1 on 2007-03-18
How do get to that "OS X" preset you were talking about?  I can't seem to find it.

---

### Post by dbbolton on 2007-03-18
it's been a long time since i've used kde... i think there is an app called KDE Settings Wizard or something similar. when you launch it, it asks whether you would like your setup to be similar to windows, mac, kde, or unix.

---

### Post by barney_1 on 2007-03-19
Great, I'll check that out.  Thanks!

---

### Post by tippit78 on 2007-03-29
In gconfig, (Menu, System Tools, Configuration Editor), look in apps, metacity, general. At the top, you can set 'action double-click titlebar'. Change it to 'minimize'.

---

### Post by OriginalGrumpyOldMan on 2007-04-07
Excellent! That worked like a charm.

Thank you, Tippit78!

---

### Post by jasonwert on 2007-06-23
Awesome, thanks a lot! I've been looking for this option for my server.

---

