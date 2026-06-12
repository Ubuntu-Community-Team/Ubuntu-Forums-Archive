---
title: "cannot install alsa 1.0.16"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by OldNewb on 2008-03-16
I have tried a couple of times to install alsa 1.0.16 I have the lib utils and driver files

following some advice I tried to install it in the /usr/local/src but I get the same errors when I try to install it anywhere.

fiyaro@fiyaro:/usr/local/src/alsa/alsa-lib-1.0.16$ sudo ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

fiyaro@fiyaro:/usr/local/src/alsa/alsa-utils-1.0.16$ sudo ./configure
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
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I am at the end of my rope on this and a step away from putting windows back on this computer.

---

### Post by Oldsoldier2003 on 2008-03-16
> **OldNewb said:**
> I have tried a couple of times to install alsa 1.0.16 I have the lib utils and driver files

following some advice I tried to install it in the /usr/local/src but I get the same errors when I try to install it anywhere.

fiyaro@fiyaro:/usr/local/src/alsa/alsa-lib-1.0.16$ sudo ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

fiyaro@fiyaro:/usr/local/src/alsa/alsa-utils-1.0.16$ sudo ./configure
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
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I am at the end of my rope on this and a step away from putting windows back on this computer.
try updating your package lists and installing build-essential

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```

---

### Post by OldNewb on 2008-03-24
> **Oldsoldier2003 said:**
> try updating your package lists and installing build-essential

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```

I ran those commands and was able to install the alsa driver and alsa lib but I can't install the alsa util file

this is what I get

fiyaro@fiyaro:/usr/local/src/alsa/alsa-utils-1.0.16$ sudo ./configure
[sudo] password for fiyaro:
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
checking for libasound headers version >= 1.0.15... found.
checking for snd_ctl_open in -lasound... yes
checking for snd_tlv_get_dB_range... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

also now I can't get to the alsa mixer and the volume adjust in the gui is telling me that I have no sound card now?

---

