---
title: "problems with ./configure  libmtp-0.1.3"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by kiwibanaan on 2007-02-19
schete@schete-desktop:~/Desktop/libmtp-0.1.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

does anyone know an answer to that problem?

---

### Post by taurus on 2007-02-19
```
sudo aptitude update
sudo aptitude install build-essential
```
Now, run your ./configure again.

---

