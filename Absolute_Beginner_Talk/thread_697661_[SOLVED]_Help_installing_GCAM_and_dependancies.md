---
title: "[SOLVED] Help installing GCAM and dependancies"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by cmittle on 2008-02-15
I've downloaded the package from [here]("http://gcam.js.cx/index.php/Files") for GCAM.  I have problems when I run ./configure so I figure the first thing to check is make sure I have the dependencies installed.  They list 3, GTK+ 2.8 or higher, OpenGL 1.1 or higher, and GtkGlExt1.0 or higher.  When I search for these in synaptic I find a lot of packages that begin with gtk but no GTK+ or gtkglext, and I can't find OpenGL.  Is there a more complete or different name that I should be searching for?  

Could someone please guide me, preferably using the command line to check versions and search the repos for these three packages?


Thank you,
Cory

---

### Post by cmittle on 2008-02-16
Apparently the GTK+ package I needed was libgtk2.0-dev.
The GtkGLext package I needed was libgtkglext1 and libgtkglext1-dev.

After installing these three packages, the ./configure command worked, then the make && make install worked, and the program now opens and seems to run appropriately.


Cory

---

