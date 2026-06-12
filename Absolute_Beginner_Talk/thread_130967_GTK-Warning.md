---
title: "GTK-Warning"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2006-02-15
When I sudo launch a script from terminal I always seem to get the error:

GTK-Warning** Can not display.

If I "open" the script with Nautilus, It works.

Is there something else I need to set up to lauch these apps from the command line?

Thanks

Seek

---

### Post by seakiwi on 2006-02-15
I can't remember the details right now, but I had the same problem recently and the answer was something along the lines of:

If you're launching a graphical application (One with a GUI)  don't use sudo - use kdesu.

Now, I don't profess to understand why that is yet but that should solve your problem I think. If I can find my original post (when I remember where I posted it)  I'll post back with the link.

---

### Post by Perfect Storm on 2006-02-15
He uses gnome, so I don't think kdesu would do any help here.

Try with gksudo

---

### Post by seekyrr on 2006-02-15
gksudo gives me the error:

(gksudo:21065):  Gtk-WARNING **: cannot open display

Thanks

Seek

---

