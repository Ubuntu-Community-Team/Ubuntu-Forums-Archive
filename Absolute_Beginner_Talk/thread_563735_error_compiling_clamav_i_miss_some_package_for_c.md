---
title: "error compiling clamav: i miss some package for c"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2007-09-30
hi,
i'm trying to update clamav but when i try to compile the tar package i get this:

***** Clamav
***** Running configure (./configure)...
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
creating target.h - canonical system defines
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) gawk
checking for gcc... gcc
checking for C compiler default output file name... 
 * configure: error: C compiler cannot create executables
 * See `config.log' for more details.
***** Return value 77

i guess i miss some packages, but i don't know what.
Please help me
thanks

---

### Post by taurus on 2007-09-30
You need the build-essential package.

```
sudo aptitude update
sudo aptitude install build-essential
./configure
```

---

### Post by MenZa on 2007-09-30
Why are you compiling ClamAV when it's already in the repositories?

```
sudo aptitude install clamav
```

---

### Post by ubunlilluz on 2007-09-30
> **MenZa said:**
> Why are you compiling ClamAV when it's already in the repositories?

```
sudo aptitude install clamav
```

yes i know, i've already this package and klamav too. Klamav said that the .deb is an obsolete version and tried to  download the last one and tried to compilie by itself, but it gave me this message.

---

