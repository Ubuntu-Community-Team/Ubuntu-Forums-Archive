---
title: "help installing zlib"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by logical_guy on 2007-03-18
Hi I tried installing zlib library and this is what I get with ./configure

Checking for gcc...
Building static library libz.a version 1.2.3 with gcc.
Checking for unistd.h... No.
Checking whether to use vs[n]printf() or s[n]printf()... using s[n]printf()
Checking for snprintf() in stdio.h... No.
  WARNING: snprintf() not found, falling back to sprintf(). zlib
  can build but will be open to possible buffer-overflow security
  vulnerabilities.
Checking for return value of sprintf()... No.
  WARNING: apparently sprintf() does not return a value. zlib
  can build but will be open to possible string-format security
  vulnerabilities.
Checking for errno.h... No.
Checking for mmap support... No.


what do i do?? thanks...

---

### Post by wesley_of_course on 2007-03-18
Wesley here ;

 Have you tried Synaptic ?

---

### Post by logical_guy on 2007-03-19
No I haven't...guess I can but I need those C/C++ libraries anyway...

---

### Post by zvacet on 2007-03-19
```
sudo aptitude install build-essential
```
In FF search engine find Ubuntu packages and type zlib.Choose one you need.

---

