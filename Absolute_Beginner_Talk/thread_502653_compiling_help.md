---
title: "compiling help"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by p3ngu1n on 2007-07-16
i am trying to compile a program and i get this:

checking build system type... i686-pc-linuxlibc1
checking host system type... i686-pc-linuxlibc1
checking target system type... i686-pc-linuxlibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


why? help?

---

### Post by Happy_Man on 2007-07-16
You are using the compilers installed using ```
sudo apt-get install build-essential
``` right?

---

### Post by p3ngu1n on 2007-07-17
why thank you :]

---

### Post by p3ngu1n on 2007-07-17
but now i get this:

root@bryce-desktop:/home/bryce/games/tuxnes-0.75# make
gcc -DHAVE_CONFIG_H -I. -I. -I.     -O -pipe -Wall -D__USE_BSD -c emu.c
emu.c: In function ‘loadpal’:
emu.c:893: error: expected ‘)’ before string constant
emu.c:915: error: expected ‘)’ before string constant
emu.c:927: error: expected ‘)’ before string constant
emu.c: In function ‘main’:
emu.c:1605: error: expected ‘)’ before string constant
make: *** [emu.o] Error 1

---

### Post by sad_iq on 2007-07-17
When you configured..no error was shown?? Maybe that step didn't go as planned!!! Try ./configure again and post any error messages!!!

---

### Post by p3ngu1n on 2007-07-17
ok so heres a look at ./configure to make:

root@bryce-desktop:/home/bryce/games/tuxnes-0.75# ./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -O ) works... yes
checking whether the C compiler (gcc -O ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for a BSD compatible install... /usr/bin/install -c
checking how to run the C preprocessor... (cached) gcc -E
checking for X... (cached) no
checking for dirent.h that defines DIR... (cached) yes
checking for opendir in -ldir... (cached) no
checking for ANSI C header files... (cached) yes
checking for features.h... (cached) yes
checking for fcntl.h... (cached) yes
checking for strings.h... (cached) yes
checking for sys/time.h... (cached) yes
checking for linux/joystick.h... (cached) yes
checking for linux/soundcard.h... (cached) yes
checking for sys/soundcard.h... (cached) yes
checking for ppm.h... (cached) no
checking for snss.h... (cached) no
checking for gzgetc in -lz... (cached) no
checking for pbm_writepbm in -lpbm... (cached) no
checking for pgm_writepgm in -lpgm... (cached) no
checking for ppm_writeppm in -lppm... (cached) no
checking for sin in -lm... (cached) yes
checking for openSnssFile in -lsnss... (cached) no
checking for ggi/gii.h... (cached) no
checking for ggi/ggi.h... (cached) no
checking for ggiInit in -lggi... (cached) no
checking for giiInit in -lgii... (cached) no
checking for Wlib.h... (cached) no
checking for w_init in -lW... (cached) no
checking whether byte ordering is bigendian... (cached) no
checking for working const... (cached) yes
checking for inline... (cached) inline
checking whether time.h and sys/time.h may both be included... (cached) yes
checking for size_t... (cached) yes
checking for 8-bit clean memcmp... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... (cached) yes
checking for working mmap... (cached) yes
checking return type of signal handlers... (cached) void
checking for gettimeofday... (cached) yes
checking for strtod... (cached) yes
checking for strtoul... (cached) yes
creating ./config.status
creating Makefile
creating config.h
config.h is unchanged
root@bryce-desktop:/home/bryce/games/tuxnes-0.75# make
gcc -DHAVE_CONFIG_H -I. -I. -I.     -O -pipe -Wall -D__USE_BSD -c emu.c
emu.c: In function ‘loadpal’:
emu.c:893: error: expected ‘)’ before string constant
emu.c:915: error: expected ‘)’ before string constant
emu.c:927: error: expected ‘)’ before string constant
emu.c: In function ‘main’:
emu.c:1605: error: expected ‘)’ before string constant
make: *** [emu.o] Error 1

---

### Post by sad_iq on 2007-07-17
Don't know for sure but try this:
 ```
sudo apt-get install autoconf
```...then configure again...and post the output!!!

---

### Post by p3ngu1n on 2007-07-17
same thing. ill just see if theres a package for this xD

---

### Post by p3ngu1n on 2007-07-17
uuh, nvm. every time i "make" something, it says it expected whatever before whatever. HELP

---

### Post by DBStevens on 2007-07-17
In the source file emu.c there are errors could you zip up that file and attach it so we can look at it?

---

