---
title: "[SOLVED] Gtk+"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2007-12-21
I am trying to install gtk and I get up to configuring it and after i runs it says

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found

what am I doing wrong?

---

### Post by Cypher on 2007-12-21
What is your command line for install GTK?

---

### Post by PeterJS on 2007-12-21
There is no "Gtk+" package, what component are you trying to install, and what are you trying to achieve?

All the gtk libs you need should be installed by default, and the package manager should handle anything that isn't there are ready.

---

### Post by chris200x9 on 2007-12-21
thanks you all but I think I have it figured out

---

### Post by chris200x9 on 2007-12-21
no no I don't

---

### Post by SOULRiDER on 2007-12-21
> **PeterJS said:**
> There is no "Gtk+" package, what component are you trying to install, and what are you trying to achieve?

All the gtk libs you need should be installed by default, and the package manager should handle anything that isn't there are ready.

Would you mind giving us that info? We may be able to help you.

---

### Post by chris200x9 on 2007-12-21
I'm following [http://library.gnome.org/devel/gtk/unstable/gtk-building.html](http://library.gnome.org/devel/gtk/unstable/gtk-building.html) I'm trying to be able to use it to learn how to make GUI's

---

### Post by PeterJS on 2007-12-21
Why? What are you trying to achieve? Is there some new feature in the development builds you need?

---

### Post by chris200x9 on 2007-12-21
No I just want to learn how to make a GUI and thought that'd be a good place to start.

---

### Post by PeterJS on 2007-12-21
Do you mean writing your own graphical applications using GTK?

---

### Post by chris200x9 on 2007-12-21
yea I have geany I thought you had to write the basics in an IDE like geany and then use GTK or something to put in the GUI....sorry if I'm just being a n00b but how would one go about learning to create a GUI for thier program?

---

### Post by PeterJS on 2007-12-21
Kinda. An IDE is really just a glorified text editor with a bunch of features useful for programming bolted on. There's nothing really special about it beyond having all the tools that you'll need in one place.

As for GTK, gtk isn't actually a program but a group of libraries that are use to create other programs. What GTK does is alot of the leg work of graphical app programming, GTK provides prebuilt functions for drawing things like buttons, text boxes, scroll bars etc.

Building your own gtk libraries just an exercise in frustration and probably not all that educational. A better place to start would be GTK Hello World:
[http://www.gtk.org/tutorial/c39.html](http://www.gtk.org/tutorial/c39.html)

There is how ever a program (and bunch of libraries) called glade for graphically creating GTK interfaces. Not real sure how it works, my understanding is that it adds some extra steps to the build process attaching the glade interface to the underlying program. Again I'm not real clear how it works, and writing the whole thing by hand would make a more educational experience.

---

### Post by chris200x9 on 2007-12-21
how do I get in to create windows like the hello world all the website tells me is: You can also view other sources of GTK information on [http://www.gtk.org/](http://www.gtk.org/). GTK uses GNU autoconf for configuration. Once untar'd, type ./configure --help to see a list of options.


Do I just type that code into my terminal? or IDE? I don't know

---

### Post by PeterJS on 2007-12-21
Paste the code in to the text editor/IDE of your choice, save it some where, and take a look at the guide to compiling hello world that's about a quarter of the way down the page:

[http://www.gtk.org/tutorial/x111.html](http://www.gtk.org/tutorial/x111.html)

---

### Post by chris200x9 on 2007-12-21
thank you very very much!

---

