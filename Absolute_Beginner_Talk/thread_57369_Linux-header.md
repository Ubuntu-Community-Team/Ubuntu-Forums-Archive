---
title: "Linux-header"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by Lambert on 2005-08-16
Ok, I keep seeing the term linux header. What is a linux-header and what does it do?

---

### Post by PeP on 2005-08-16
A header is a special part of a code where you declare functions, and variables.
To use a library from an other package, you include it's headers in your code, and then just use the functions.

You do not need the eaders to run ubuntu, however, if you want to compile a program, (the ./configure/make/sudo checkinstall way), you will then need the headers.

Typically, to compile a kernel module, you need linux-headers. Most of the drivers are or include kernel modules.

If you want to compile amarok you will need headers for kde-multimedia and gstreamer.

---

