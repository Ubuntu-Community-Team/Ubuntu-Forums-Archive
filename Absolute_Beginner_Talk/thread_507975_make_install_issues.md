---
title: "make install issues"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Flyingroof on 2007-07-23
I'm installing GCC and I did the ./configure with all the libraries and then the make and everything seems fine. So after what felt like hours of waiting for the make code to finish I type in make install and get this:

```
/bin/sh ./mkinstalldirs /usr/local /usr/local
cd: 5: can't cd to host-i686-pc-linux-gnu/fixincludes
make[1]: *** [install-fixincludes] Error 2

```
anyone know what I did wrong there?

---

### Post by ddrichardson on 2007-07-23
did you issue the make install command as sudo?

---

