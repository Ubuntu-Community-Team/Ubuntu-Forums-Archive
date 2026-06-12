---
title: "Allegro doesn't work"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by aoiz on 2006-05-31
I have already installed allegro and taken all necessary steps documented in the build-docs.
When I try to compile 'gcc file.c -lalleg', it simply says "cannot find -lalleg "

Did I miss any configurations?

---

### Post by Zdravko on 2006-05-31
Hm, maybe. I remember compiling and running an Allegro application in Ubuntu 5.10 - with no problems at all. The "alleg" library may be unknown to the compiling system. Try to specify it explicitely.

---

### Post by aoiz on 2006-05-31
By what means could I specify the argument -lalleg further?

---

### Post by GeoMX on 2006-07-09
Try like this:

> 
gcc file.c `allegro-config --cflags` `allegro-config --libs`


Best wishes.

---

### Post by ios_base on 2007-05-01
wow!  That solved my problem too!  Where and how did you find this out?

---

