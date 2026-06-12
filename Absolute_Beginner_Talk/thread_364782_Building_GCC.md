---
title: "Building GCC"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-02-18
I am attempting to install the GCC package from the site: [http://gcc.gnu.org/java/](http://gcc.gnu.org/java/).
The prerequsites listed on installation instructions require the mpfr library. When I try in run the configure option I get the following warnings:

configure: WARNING: 'gmp.h' and 'libgmp' seems to have different versions or
configure: WARNING: we cannot run a program linked with GMP (if you cannot
configure: WARNING: see the version numbers above).
configure: WARNING: However since we can't use 'libtool' inside the configure,
configure: WARNING: we can't be sure. See 'config.log' for details.


I attempted continue by using make to build the mpfr library and then used make check at which point 115/117 tests were reported failed. Can some one help me with this?

---

### Post by m.musashi on 2007-02-18
If you just want to install gcc, it is in the repositories. Just 
```
sudo apt-get install gcc
```
and you'll be good to go.

Conversely, you might
```
sudo apt-get install build-essential
```
to get all the required packages for compiling and such.

---

### Post by noorez on 2007-02-18
I have already done this, but when I compared the version numbers, the one avalible by source is more recent then the one that is avalible by apt-get

---

### Post by m.musashi on 2007-02-18
That's possible. The ones in the repos are usually not the most recent. It takes them a while to update and in some cases they may never. I don't really know the ins and outs of that. Although it is probably related to testing and packaging and making sure it's going to work like it's supposed to. However, unless you have a specific need for the most up-to-date version the one in the repo should do just fine. It's what just about everyone else is using.

---

