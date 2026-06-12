---
title: "Installing Package Using Make"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-01-19
I am tryin to install the [Baghira]("http://www.kde-look.org/content/show.php?content=8692") theme but I am having a hard time.

As written in the page from kde-look.org:
> Installation
-----------------
tar -xjf baghira.tar.bz2
cd baghira/baghira
./configure --prefix=`kde-config --prefix` --disable-debug [--enable-final]
(!!!BEGINNERS: the direction of the accents is _important_ (top-left to bottom-right), the rectangular brackets mean [this is optional] - don't type them!!!)
make
and finally as root:
make install

after going to the directory, I entered ./configure --prefix=`kde-config --prefix` --disable-debug
```
user@Laptop:/tmp/fr-MlzNRh/baghira-0.8$ ./configure --prefix=`kde-config --prefix` --disable-debug
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as requested)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

```

Then, I entered "make"
```
user@Laptop:/tmp/fr-MlzNRh/baghira-0.8$ make
make: *** No targets specified and no makefile found.  Stop.
user@Laptop:/tmp/fr-MlzNRh/baghira-0.8$

```

What do I do next?

---

### Post by Pobega on 2007-01-19
> configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

What's in your config.log?

---

### Post by wersdaluv on 2007-01-19
> **Pobega said:**
> What's in your config.log?

Where can I find the config.log?

---

