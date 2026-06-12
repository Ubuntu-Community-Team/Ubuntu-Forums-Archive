---
title: "[SOLVED] ./configure giving an error pls help"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by arjayes on 2007-10-28
this is what i get when i try to run the configure script for currenttrack i get the same for other installs as well is there something wrong with the c compiler  





[03:05 PM]ratan@Ratan-Laptop:~/Desktop/currenttrack-1.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


pls help

---

### Post by mali2297 on 2007-10-28
Have you installed build-essential?
```

sudo apt-get install build-essential

```

---

### Post by Maestro23 on 2007-10-28
Do you have build-essential installed?

> sudo apt-get install build-essential

---

### Post by arjayes on 2007-10-28
Thanks that worked
could u pls tell me what exactly build-essential is?
:)

---

### Post by mali2297 on 2007-10-28
> **arjayes said:**
> Thanks that worked
could u pls tell me what exactly build-essential is?
:)

It is a dummy package that will install the C compiler together with the essential things for compilation.

---

### Post by Maestro23 on 2007-10-28
> **mali2297 said:**
> It is a dummy package that will install the C compiler together with the essential things for compilation.

Just to add, if the OP wants more info, look it up in Synaptic.:guitar:

---

