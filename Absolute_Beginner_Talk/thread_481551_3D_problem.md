---
title: "3D problem"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by pascalosti on 2007-06-22
Can someone tell me if there is a package that will install all the 3d stuff.

My video card is ati x600.  On my previous Ubuntu install I installed everything to do with OpenGL, and GtkGlext, with no success.

(get this error when trying to view chess in 3D)
install the OpenGL Python bindings and the GtkGLExt Python bindings.

---

### Post by DBStevens on 2007-06-23
The OpenGL Python bindings 

is the python-opengl package

I haven't found the other one yet

---

### Post by DBStevens on 2007-06-23
The other one is possibly:

libgtkglextll

I haven't come across any package in the normal repos and there is an unanswered bug report for that  package being missing.

A bit of Google fu indicates such a binding package being available for freebsd.  

It might be worth while searching various repos for it.

---

