---
title: "C++ making a gui tut?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-10-11
Anyone have any good tutorials for making a C++ gui using G++ compiler? Not for windows, this is a linux gui.

---

### Post by skymt on 2006-10-11
GTK or QT? For QT, the official Trolltech tutorial is helpful ([3.3](http://doc.trolltech.com/3.3/tutorial.html), [4.1](http://doc.trolltech.com/4.1/tutorial.html); KDE currently uses 3.3). For GTK, you want gtkmm, the C++ bindings. They also have [a tutorial](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html).

---

### Post by Ben Sprinkle on 2006-10-11
All I have now is gcc+.
I just read that gtk and that q thing are like extentions to gcc+?
Anyway which is better, Q or GTK? How to use install etc?

---

### Post by skymt on 2006-10-11
GTK and QT are "toolkits". They're basically frameworks for GUI applications. Gnome (the Ubuntu default desktop environment) uses GTK, KDE (the default in Kubuntu) uses QT. If you use Gnome, use GTK/gtkmm. If you use KDE, use QT.

You already have one or the other installed. You probably don't have the headers or other developer files. To get those, install libgtkmm-2.4-dev (for gtkmm), qt3-dev-tools and libqt3-mt-dev (for QT 3.3), or libqt4-dev (for QT 4).

---

### Post by fatsheep on 2006-10-11
It's a matter of personal preference.  I prefer GTK but there are a lot of QT fans out there as well otherwise KDE wouldn't be so popular.

---

### Post by Ben Sprinkle on 2006-10-11
Well I have kubuntu, and already installed gtk and gtkmm. :)
Will try QT some other time.

---

