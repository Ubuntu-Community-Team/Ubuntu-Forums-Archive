---
title: "setting up ALSA"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by fiat42lux on 2008-03-24
I have an EMU 1616. According to [this list]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs"), it should be supported by ALSA starting from 1.0.15. Following [this]("http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga") tutorial, I've downloaded and extracted the ALSA 1.0.16 sources. But when I try to make:
```
root@Elbeest:/usr/src/alsa/alsa-utils-1.0.16# ./configure ; make ; make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.15... not present.
configure: error: Sufficiently new version of libasound not found.
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
root@Elbeest:/usr/src/alsa/alsa-utils-1.0.16# 
```
But I do!:
```
root@Elbeest:/usr/src/alsa/alsa-utils-1.0.16# ldconfig -v | grep libasound
        libasound.so.2 -> libasound.so.2.0.0
```
I also tried
```
root@Elbeest:/usr/src/alsa/alsa-utils-1.0.16# apt-get install build-essential libasound2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libasound2-dev is already the newest version.
```
So how am I supposed to get an even newer version? Your help would be greatly appreciated.

---

### Post by Junglizer on 2008-03-24
Which Linux distro/version are you running? And are you sure you don't have ALSA in the kernel? If you are running Ubuntu I would assume that they have it in the kernel, you can either use ALSA built-in(/modules too) or compile from source, but you'll get errors if you have it in the kernel and try to compile the source. Thats really all I can offer for help :'(

---

### Post by Junglizer on 2008-03-24
So if you've got ALSA somewhere, ```
alsaconf
``` should usually work for auto-configuration and usually works for finding the right card.

---

