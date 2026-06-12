---
title: "OpenGL and Chess"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Samurai Penguin on 2008-03-21
glChess 2.20.0.1 comes already installed on Ubuntu 7.10

When I ran it and tried to switch to 3D view it gave the following:

Unable to Enable 3D Mode
Your system does not have the required software to enable 3D mode. 
Please contact your system administrator and ask them to install the 
OpenGL Python bindings and the GtkGLExt Python bindings.

glChess 2.20.0.1
The 2D/3D chess game for GNOME
glChess is a part of GNOME Games

I already installed Resrticted Drivers for the ATI X1600 card.
Where do I get the OpenGL files for Python and how are they 
installed?

---

### Post by Neo0351 on 2008-03-21
This should work 
```
 sudo apt-get install python-opengl python-gtkglext1 

```

---

### Post by Samurai Penguin on 2008-03-22
yup, that did it ...thanks

---

