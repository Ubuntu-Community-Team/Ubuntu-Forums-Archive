---
title: "an xlib problem... i think"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by cl3ellio on 2006-05-04
So I'm trying to use geomview (3-D viewer) through some CGAL (geometry library) demos. But after starting up geomview I get the following messages:

Starting Geomview...done.
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Geomview: internal error: Illegal instruction; dump core now (y/n) [n] ? n
Warning: XtRemoveGrab asked to remove a widget not on the list
Warning: XtRemoveGrab asked to remove a widget not on the list
Warning: XtRemoveGrab asked to remove a widget not on the list

I think this is a problem with xlib (xorg I'm not sure what is what, does anybody have a good link explaining all x graphical stuff?), because when I try and use startx I get:

xauth:  creating new authority file /home/chris/.serverauth.27525

X: user not authorized to run the X server, aborting.

Is there a package I should get? Any ideas as to what I'm missing?

---

