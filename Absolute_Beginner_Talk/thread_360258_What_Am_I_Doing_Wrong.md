---
title: "What Am I Doing Wrong?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Blue_Sky on 2007-02-12
Hi,
I'm trying to install the Avant Window Navigator. I tried using alien to install it outright, but after trying to use the terminal to start it and then searching the hard drive, it didn't seem installed. I tried using the package manager that is default for .deb files, and it told me that both files were installed, so I reinstalled them. Again, no dice. Are the installed files unsearchable (even with hidden and backup files shown) and does the terminal command not have anything to do with "awn", "avant" or "avant-window-navigator", or are the files really not installing?
I'm running beryl, if that makes any difference.

Blue

---

### Post by sunexplodes on 2007-02-12
search for it in Synaptic. If you find it and it claims to be installed, right-click the entry, go to properties. Then look in the Installed files tab, and look for an entry in /usr/bin. 

try and run that entry in terminal, and see what happens.

---

### Post by Blue_Sky on 2007-02-13
Ok, I checked and there is no entry for /usr/bin.
This is what there is:

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/avant-window-navigator
/usr/share/doc/avant-window-navigator/copyright
/usr/share/doc/avant-window-navigator/changelog.Debian.gz
/avant-window-navigator-0.1.1.tar.gz
/avant-window-navigator.spec

I'm not sure what to do next.

---

### Post by sunexplodes on 2007-02-13
Well my friend, I don't know why your method didn't work, but I found a new method for you, and i've tested it myself, so it should work. 

There's a deb file for it at the following link, which installed quite well on my edgy machine. [http://blog.paulbetts.org/index.php/2007/02/01/avant-window-navigator-for-ubuntu-edgy/](http://blog.paulbetts.org/index.php/2007/02/01/avant-window-navigator-for-ubuntu-edgy/)

---

### Post by Blue_Sky on 2007-02-13
Ok, its working. There is a problem with the icons of open programs and it quits randomly, but I'll have a look at other threads to see what is happening. BTW, the error I'm getting is (after downloading a patch - "awn.diff"): 

 Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

(avant-window-navigator:12820): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

---

