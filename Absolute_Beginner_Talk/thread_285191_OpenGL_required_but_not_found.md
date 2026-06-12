---
title: "OpenGL required but not found"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Mankua on 2006-10-26
Hello,

I am trying to build and install K-3D (a 3D application) that uses OpenGL. In the ./configure step it stops with this error:

checking for OpenGL... configure: error: OpenGL required but not found

I looked into the configure code and it is searching for this file:

libGL.so

I don't have that file, but I have 
/usr/lib/libGL.so.1

I can't find the /GL/ folder either, or the gl.h header.

I installed the nvidia packages for OpenGL, but that didn't install any of these files... 

Any ideas? Where can I find the OpenGL libraries? 

Thank you
diego

---

### Post by Iarwain ben-adar on 2006-10-27
Hi,
and welcome ;)

Just a question,
why don't you install via aptitude?
```
sudo aptitude install k3d
```

It's waaaay easier via aptitude than any other way :D


Iarwain

---

