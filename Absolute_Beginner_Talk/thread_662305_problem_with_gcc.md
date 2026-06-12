---
title: "problem with gcc?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by bat3man on 2008-01-08
I am trying to install the GNU scientific library, but when I try to use ./configure, I get:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Can anyone help?
Thanks

---

### Post by chippy99 on 2008-01-08
Have you installed the GCC compiler ?

If not type sudo apt-get install build-essential

---

### Post by bat3man on 2008-01-09
Thanks, that got me past one stage (I had tried to check that gcc was installed, but I guess I failed at that...).

Now though, when I try to "make," it seems to get caught in an endless loop.

Am I making another very green mistake?

---

