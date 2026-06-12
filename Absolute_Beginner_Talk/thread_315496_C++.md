---
title: "C++"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-12-09
I'm running Xubuntu, and I need a program to write C++ and a compiler like Dev C++.  Anyone wanna help me? thanks

---

### Post by bscbrit on 2006-12-09
For an environment to work in, look at kdevelop or anjuta.  The compiler is g++.

---

### Post by huwnet on 2006-12-09
I'd recommend codeblocks although the stable version is a bit outdated so you might want to download the source or a nightly deb from the site

---

### Post by Lord Illidan on 2006-12-09
Dev-C++ is not a compiler, it is an IDE which uses the MinGW compiler (a port of GCC to windows)

To install an IDE and a c++ compiler, use apt-get or synaptic.

First run

sudo apt-get install build-essential

then sudo apt-get install anjuta

and get cracking..

---

