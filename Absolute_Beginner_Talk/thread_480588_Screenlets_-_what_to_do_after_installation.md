---
title: "Screenlets - what to do after installation??"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-06-21
I think I succeeded in screenlets installation... at least when I go to Synaptic I see screenlets listed in green.  But where are they?  How do I turn them on?  They are not listed under any menus and I don't see anything extra on my desktop.  Do I have to install something extra or all of them are within the package and I just don't know how to turn them on???

Thanx!

---

### Post by diatribe on 2007-06-21
if its not in the menus run screenletsd from a console, then right click the icon in your system tray and add whichever ones you want

---

### Post by arvevans on 2007-06-21
From a terminal screen:
[INDENT]gnome-screenshot --interactive
[/INDENT]

If that works, then you need to build a launcher for it.  The launcher should have been added to:
[INDENT]Applications/Accessories/Take Screenshot[/INDENT]
when it installed.
_._

---

