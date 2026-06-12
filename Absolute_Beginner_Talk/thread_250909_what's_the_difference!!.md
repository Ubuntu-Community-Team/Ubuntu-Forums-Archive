---
title: "what's the difference!!??"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by k9brand on 2006-09-04
I just don't understand what the difference between the following:

GTK
GDM
MetaCity
XGL
X

What can work together?  What do you **have** to run and what is extra?

---

### Post by Jussi Kukkonen on 2006-09-04
You dont *have* to run any of those -- won't have a graphical user interface then though.

X is the window system protocol. X.org is the canonical implementation that pretty much all window managers and desktop environments use. X takes care of drawing and moving windows on the screen and handling a mouse and/or keyboard.

GDM is a display manager. It handles sessions, allows  you to login and so on. You need a display manager to work with X AFAIK. The default display manager for X is XDM, but gnome uses GDM.

GTK is a the toolkit used to build the gnome GUI. It provides the buttons, drop-down boxes and other widgets gnome applications use. 

Metacity is the window manager for gnome. A WM  controls the placement of windows on screen and one must be running for X to work, AFAIK. Metacity uses GTK.

XGL is a X implementation that uses OpenGL and hardware acceleration.

---

### Post by steve.horsley on 2006-09-04
My wild guesses:

GTK
Gnome Tool Kit
A library of graphical drawing software. Allows applications to easily create buttons, textboxes, sliders and other such graphical components. I think all Gnome applications use GTK (or GTK2). GTK was originally developed for the graphics application GIMP, and re-used by many other applications later on.
[http://en.wikipedia.org/wiki/GTK](http://en.wikipedia.org/wiki/GTK)

GDM
Gnome Desktop Manager
A graphical login utility that collects your username and password, then (if it likes you) launches a proper X session for you using your user ID. Looks nicer than a B&W text login screen.

Metacity
The default Gnome window manager. This is the software that re-sizes windows, brings them to the fromt/back when you click them and stuff like that. 
[http://en.wikipedia.org/wiki/Metacity](http://en.wikipedia.org/wiki/Metacity)

X
The low-level graphical display protocol / server. Software calls to X include such low-level things as draw a line, deaw a circle, paint this bitmep here (I think). 
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

XGL
A new implementation of X that uses the hardware 3d-acceleration features of graphics cards to draw stuff faster, using the OpenGL 3d drawing library.
[http://en.wikipedia.org/wiki/XGL](http://en.wikipedia.org/wiki/XGL)

Being pedantic, none of this is mandatory - you can get by with a 24x80 text window for a lot of things.

If you want graphics, you need X, and you really need a window manager. Applications written for GTK need GTK of course, but there are many other graphical widget toolkits around.

---

