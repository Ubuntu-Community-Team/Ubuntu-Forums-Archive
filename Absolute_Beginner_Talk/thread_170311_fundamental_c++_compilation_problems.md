---
title: "fundamental c++ compilation problems"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by bodhidharma on 2006-05-04
Hey, friends, I have a weird problem with compiling some source from
sourceforge (ht://Dig): running the usual "./configure" gives information
that it cannot find iostream.h and a few other critical files, and it tells
me I have to install libstdc++ (which I have installed).  Someone on
the ht://Dig mailing list suggested using"CXXFLAGS=-Wno-deprecated
CPPFLAGS=-Wno-deprecated", which worked (although there were a
heap of warnings about this being an invalid option for c, only valid for
c++).  My question is: what's up?  Why cannot I compile a piece of
standard, up-to-date software just out of the box on my (standard,
up-to-date) Ubuntu 5.10?

Thanks

---

### Post by linear on 2006-05-04
Did you install the **build-essential** package? If not, that's the problem.

---

