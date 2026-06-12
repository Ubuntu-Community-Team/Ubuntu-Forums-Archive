---
title: "cant link to libgl.so ??"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-03-10
im tring to build some opengl code that worked on windows. So when i got to build it, all compiles well but when i try to link i get this: 

Building target: Objloader
Invoking: GCC C++ Linker
gcc -L/usr/lib -oObjloader ./Main.o ./ObjLoader.o -lGL -lglut -lglu
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [Objloader] Error 1
make: Target `all' not remade because of errors.

ive doubled checked many times libGL.so.1 and libGL.so.1.2 are in /usr/lib

any help would be great, thanks!

---

### Post by Pragmatist on 2006-03-11
I'm confused.  Why are you using GL rather than the filename?  Also, can you try an absolute path after the -l (even though you specified -L/usr/lib)  I didn't see anything in the GCC man page that precluded that.

---

