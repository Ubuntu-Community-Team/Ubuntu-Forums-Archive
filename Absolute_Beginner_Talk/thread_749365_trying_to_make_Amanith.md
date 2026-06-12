---
title: "trying to make Amanith"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Mr T 87 on 2008-04-08
I've being trying to build amanith 0.3 for 2 days. I've tried installing it with QT3 and QT4 and both produce similar problems. I use the command qmake amanith.pro and then make and it ends a little something like this after a couple of minutes...

```
../../../include/amanith/geometry/gmatrix.h:2418:   instantiated from here
../../../include/amanith/geometry/gmatrix.h:326: warning: dereferencing type-punned pointer will break strict-aliasing rules
make[3]: *** [main.o] Error 1
make[3]: Leaving directory `/home/tesh/amanith/examples/opengl/vectorizer'
make[2]: *** [sub-vectorizer-make_default-ordered] Error 2
make[2]: Leaving directory `/home/tesh/amanith/examples/opengl'
make[1]: *** [sub-opengl-make_default-ordered] Error 2
make[1]: Leaving directory `/home/tesh/amanith/examples'
make: *** [sub-examples-make_default-ordered] Error 2

```

Anyone have any idea how to fix these errors?

Thanks in advance :)

---

