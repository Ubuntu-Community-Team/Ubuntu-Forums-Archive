---
title: "Trouble compiling qt4 from source..."
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by prophet001 on 2007-05-12
Hi, I posted this in the programming forum as well, but when I try to run make on QT4 under Feisty Fawn, I get these errors:

make[3]: *** [.obj/debug-shared/qapplication.o] Error 1
make[3]: Leaving directory `/home/ben/qt-x11-opensource-src-4.0.1/src/gui'
make[2]: *** [debug-all] Error 2
make[2]: Leaving directory `/home/ben/qt-x11-opensource-src-4.0.1/src/gui'
make[1]: *** [sub-gui-make_default-ordered] Error 2
make[1]: Leaving directory `/home/ben/qt-x11-opensource-src-4.0.1/src'
make: *** [sub-src-make_default-ordered] Error 2

Does anyone know what I need to change to get it to work?

---

### Post by FuturePast on 2007-05-13
There should be more errors than that, ocurring earlier in the process.

---

### Post by prophet001 on 2007-05-13
Well, there were a few, but to get them I would have to run make again and that takes about 20 minutes...is there a manpage floating around anywhere that covers these errors?

---

### Post by FuturePast on 2007-05-13
Well, at the risk of stating the obvious, it depends on exactly what the error is.
At some point in the build there will be a fatal error, all other errors after that are irrelevant.
It will probably be a compilation error from gcc.

Find the first error and stick it into google.

---

### Post by prophet001 on 2007-05-13
Ok thanks. I'm using g++, btw.

---

### Post by ramjet_1953 on 2007-05-13
Two questions:

Why do you want to compile it from source, when it's available for download in the repostiories, using Synaptic?

If you do still want to "roll your own", have you installed the [COLOR="Blue"]build-essential[/COLOR] package, which is also in the repositories?

Regards,
Roger 8)

---

