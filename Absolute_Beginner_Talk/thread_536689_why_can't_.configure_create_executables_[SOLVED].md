---
title: "why can't ./configure create executables? [SOLVED]"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Drone4four on 2007-08-28
When I try to configure  a GTK theme, I get this error:

```
drone4four@kubuntu:~/gui/aurora-1.2$ ./configure --prefix=/usr -enable-animation
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
drone4four@kubuntu:~/gui/aurora-1.2$   
```
How do I create executables?

---

### Post by bvmou on 2007-08-28
You probably need to install the package build-essential, which you can do by 'sudo apt-get install build-essential'  -- this is a catch-all package that has as dependencies many packages that are necessary to build from source.  Try to run ./configure after installing build-essential.  (The package includes c and c++ compilers and libraries and the make utility).

---

### Post by Drone4four on 2007-08-28
that worked, thanks bvmou

---

