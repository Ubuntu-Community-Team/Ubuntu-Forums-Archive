---
title: "Gens compiling error"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by GSZX1337 on 2008-02-08
I'm trying to compile Gens from Source and every time I try, I get  this:

```
gszx1337@G-Man:~$ cd '/home/gszx1337/Desktop/GensForLinux' 
gszx1337@G-Man:~/Desktop/GensForLinux$ sudo make install
[sudo] password for gszx1337:
Making install in src
make[1]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src'
Making install in starscream
make[2]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
Making install in main68k
make[3]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
make[4]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
make[3]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
Making install in sub68k
make[3]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[4]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[3]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[3]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
make[4]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
make[3]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
make[2]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
Making install in gens
make[2]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/gens'
source='gens_core/cpu/68k/cpu_68k.c' object='gens_core/cpu/68k/gens-cpu_68k.o' libtool=no \
        depfile='.deps/gens_core/cpu/68k/gens-cpu_68k.Po' tmpdepfile='.deps/gens_core/cpu/68k/gens-cpu_68k.TPo' \
        depmode=gcc3 /bin/bash ../../depcomp \
        gcc-3.4 -DHAVE_CONFIG_H -I. -I. -I../.. -I./gens_core/cpu/68k -I./gens_core/cpu/sh2 -I./gens_core/cpu/z80 -I./gens_core/sound -I./gens_core/mem -I./gens_core/misc -I./gens_core/gfx -I./gens_core/io -I./gens_core/vdp -I./segacd -I./mp3_dec -I./sdllayer -I./util -I./port -I./emulator -I./debug -I./netplay -I./gtkui -I./gtkui/anjuta_widget -I./gtkui/glade -I.   -DDATADIR=\"/usr/local/share/gens\" -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -g -O2 -g -O2 -c -o gens_core/cpu/68k/gens-cpu_68k.o `test -f gens_core/cpu/68k/cpu_68k.c || echo './'`gens_core/cpu/68k/cpu_68k.c
gens_core/cpu/68k/cpu_68k.c:27: warning: initializer element is not computable at load time
gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for `M68K_Fetch[1].offset')
gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for `M68K_Fetch[1]')
gens_core/cpu/68k/cpu_68k.c:28: warning: initializer element is not computable at load time
gens_core/cpu/68k/cpu_68k.c:28: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:28: error: (near initialization for `M68K_Fetch[2].offset')
gens_core/cpu/68k/cpu_68k.c:28: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:28: error: (near initialization for `M68K_Fetch[2]')
gens_core/cpu/68k/cpu_68k.c:29: warning: initializer element is not computable at load time
gens_core/cpu/68k/cpu_68k.c:29: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:29: error: (near initialization for `M68K_Fetch[3].offset')
gens_core/cpu/68k/cpu_68k.c:29: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:29: error: (near initialization for `M68K_Fetch[3]')
gens_core/cpu/68k/cpu_68k.c:30: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:30: error: (near initialization for `M68K_Fetch[4]')
gens_core/cpu/68k/cpu_68k.c:31: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:31: error: (near initialization for `M68K_Fetch[5]')
gens_core/cpu/68k/cpu_68k.c:32: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:32: error: (near initialization for `M68K_Fetch[6]')
gens_core/cpu/68k/cpu_68k.c:63: warning: initializer element is not computable at load time
gens_core/cpu/68k/cpu_68k.c:63: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:63: error: (near initialization for `S68K_Fetch[0].offset')
gens_core/cpu/68k/cpu_68k.c:63: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:63: error: (near initialization for `S68K_Fetch[0]')
gens_core/cpu/68k/cpu_68k.c:64: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:64: error: (near initialization for `S68K_Fetch[1]')
gens_core/cpu/68k/cpu_68k.c:65: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:65: error: (near initialization for `S68K_Fetch[2]')
gens_core/cpu/68k/cpu_68k.c: In function `M68K_Set_32X_Rom_Bank':
gens_core/cpu/68k/cpu_68k.c:365: warning: cast from pointer to integer of different size
gens_core/cpu/68k/cpu_68k.c: In function `M68K_Set_Prg_Ram':
gens_core/cpu/68k/cpu_68k.c:390: warning: cast from pointer to integer of different size
make[2]: *** [gens_core/cpu/68k/gens-cpu_68k.o] Error 1
make[2]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/gens'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src'
make: *** [install-recursive] Error 1

```

EDIT: I have a AMD 64 machine, therefore, I cannot use a.deb.

---

### Post by spiderbatdad on 2008-02-08
i was  just looking at the source. There is a configure and make file. Are you skipping those steps, or have you already run them without error?

---

### Post by jan quark on 2008-02-08
compiling are these three commands
run in that order


```
./configure
```
```
sudo make
```
```
sudo make install
```

---

### Post by samwyse on 2008-02-08
make shouldn't be run with sudo.

---

### Post by GSZX1337 on 2008-02-08
> **jan quark said:**
> compiling are these three commands
run in that order


```
./configure
```
```
sudo make
```
```
sudo make install
```

When I type 
```
./configure
```

I get:

```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.4.0... yes (version 2.12.0)
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.1.3... yes
checking for nasm... /usr/bin/nasm
checking for clock_gettime in -lrt... yes
checking for getopt in -lc... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating pixmaps/Makefile
config.status: creating src/Makefile
config.status: creating src/gens/Makefile
config.status: creating src/starscream/Makefile
config.status: creating src/starscream/main68k/Makefile
config.status: creating src/starscream/sub68k/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands

```

When I type

```
sudo make
```

I get:

```
cd . \
          && CONFIG_FILES= CONFIG_HEADERS=config.h \
             /bin/bash ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
make  all-recursive
make[1]: Entering directory `/home/gszx1337/Desktop/GensForLinux'
Making all in src
make[2]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src'
Making all in starscream
make[3]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
Making all in main68k
make[4]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
make  all-am
make[5]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
make[4]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
Making all in sub68k
make[4]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make  all-am
make[5]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[4]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[4]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
make[3]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
Making all in gens
make[3]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/gens'
source='gens_core/cpu/68k/cpu_68k.c' object='gens_core/cpu/68k/gens-cpu_68k.o' libtool=no \
        depfile='.deps/gens_core/cpu/68k/gens-cpu_68k.Po' tmpdepfile='.deps/gens_core/cpu/68k/gens-cpu_68k.TPo' \
        depmode=gcc3 /bin/bash ../../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I./gens_core/cpu/68k -I./gens_core/cpu/sh2 -I./gens_core/cpu/z80 -I./gens_core/sound -I./gens_core/mem -I./gens_core/misc -I./gens_core/gfx -I./gens_core/io -I./gens_core/vdp -I./segacd -I./mp3_dec -I./sdllayer -I./util -I./port -I./emulator -I./debug -I./netplay -I./gtkui -I./gtkui/anjuta_widget -I./gtkui/glade -I.   -DDATADIR=\"/usr/local/share/gens\" -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -g -O2 -g -O2 -c -o gens_core/cpu/68k/gens-cpu_68k.o `test -f gens_core/cpu/68k/cpu_68k.c || echo './'`gens_core/cpu/68k/cpu_68k.c
gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for ‘M68K_Fetch[1].offset’)
gens_core/cpu/68k/cpu_68k.c:28: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:28: error: (near initialization for ‘M68K_Fetch[2].offset’)
gens_core/cpu/68k/cpu_68k.c:29: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:29: error: (near initialization for ‘M68K_Fetch[3].offset’)
gens_core/cpu/68k/cpu_68k.c:63: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:63: error: (near initialization for ‘S68K_Fetch[0].offset’)
gens_core/cpu/68k/cpu_68k.c: In function ‘M68K_Set_32X_Rom_Bank’:
gens_core/cpu/68k/cpu_68k.c:365: warning: cast from pointer to integer of different size
gens_core/cpu/68k/cpu_68k.c: In function ‘M68K_Set_Prg_Ram’:
gens_core/cpu/68k/cpu_68k.c:390: warning: cast from pointer to integer of different size
make[3]: *** [gens_core/cpu/68k/gens-cpu_68k.o] Error 1
make[3]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/gens'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gszx1337/Desktop/GensForLinux'
make: *** [all] Error 2

```

And when I type 

```
sudo make install
```

I get:

```
Making install in src
make[1]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src'
Making install in starscream
make[2]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
Making install in main68k
make[3]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
make[4]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
make[3]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/main68k'
Making install in sub68k
make[3]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[4]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[3]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream/sub68k'
make[3]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
make[4]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
make[3]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
make[2]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/starscream'
Making install in gens
make[2]: Entering directory `/home/gszx1337/Desktop/GensForLinux/src/gens'
source='gens_core/cpu/68k/cpu_68k.c' object='gens_core/cpu/68k/gens-cpu_68k.o' libtool=no \
        depfile='.deps/gens_core/cpu/68k/gens-cpu_68k.Po' tmpdepfile='.deps/gens_core/cpu/68k/gens-cpu_68k.TPo' \
        depmode=gcc3 /bin/bash ../../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I./gens_core/cpu/68k -I./gens_core/cpu/sh2 -I./gens_core/cpu/z80 -I./gens_core/sound -I./gens_core/mem -I./gens_core/misc -I./gens_core/gfx -I./gens_core/io -I./gens_core/vdp -I./segacd -I./mp3_dec -I./sdllayer -I./util -I./port -I./emulator -I./debug -I./netplay -I./gtkui -I./gtkui/anjuta_widget -I./gtkui/glade -I.   -DDATADIR=\"/usr/local/share/gens\" -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -g -O2 -g -O2 -c -o gens_core/cpu/68k/gens-cpu_68k.o `test -f gens_core/cpu/68k/cpu_68k.c || echo './'`gens_core/cpu/68k/cpu_68k.c
gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for ‘M68K_Fetch[1].offset’)
gens_core/cpu/68k/cpu_68k.c:28: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:28: error: (near initialization for ‘M68K_Fetch[2].offset’)
gens_core/cpu/68k/cpu_68k.c:29: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:29: error: (near initialization for ‘M68K_Fetch[3].offset’)
gens_core/cpu/68k/cpu_68k.c:63: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:63: error: (near initialization for ‘S68K_Fetch[0].offset’)
gens_core/cpu/68k/cpu_68k.c: In function ‘M68K_Set_32X_Rom_Bank’:
gens_core/cpu/68k/cpu_68k.c:365: warning: cast from pointer to integer of different size
gens_core/cpu/68k/cpu_68k.c: In function ‘M68K_Set_Prg_Ram’:
gens_core/cpu/68k/cpu_68k.c:390: warning: cast from pointer to integer of different size
make[2]: *** [gens_core/cpu/68k/gens-cpu_68k.o] Error 1
make[2]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src/gens'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/gszx1337/Desktop/GensForLinux/src'
make: *** [install-recursive] Error 1

```

---

### Post by macogw on 2008-02-08
You hit the error on make, so of course make install isn't going to work.

Anyway, the errors look like regular old compile errors, the kind you get when you write bad code.

---

### Post by lswest on 2008-02-08
do you have the build-essential package installed? install with: ```
sudo apt-get install build-essential
```

---

### Post by macogw on 2008-02-08
> **lswest said:**
> do you have the build-essential package installed? install with: ```
sudo apt-get install build-essential
```

If s/he got far enough through compiling to get a compiler error, probably.

---

### Post by GSZX1337 on 2008-02-08
> **macogw said:**
> If he got far enough through compiling to get a compiler error, probably.

Yes, I have the build essential package installed.

---

### Post by fenian on 2008-02-08
There is a .deb of the latest gens available[ here]("http://www.zshare.net/download/477181507f7e3b/").Works well for me in gutsy.

---

### Post by mc4man on 2008-02-08
maybe this will help - slightly dated, what _may_ be of interest is > Gens WILL NOT COMPILE with the standard gcc-4.0 that comes in Dapper and later versions of Ubuntu. To make sure that Gens gets built with gcc-3.4, ......]
[http://saquibhussain.multiply.com/journal/item/23](http://saquibhussain.multiply.com/journal/item/23)

---

### Post by GSZX1337 on 2008-02-08
> **mc4man said:**
> maybe this will help - slightly dated, what _may_ be of interest is 
[http://saquibhussain.multiply.com/journal/item/23](http://saquibhussain.multiply.com/journal/item/23)

I have found that tutorial. How can I have Gens built with gcc-3.4?

---

### Post by mc4man on 2008-02-08
took a few tries (missing some packages)
```
CC=gcc-3.4 ./configure
```
works for configure  (need gcc-3.4 packages)
note - I'm on 32bit

here's a configure to compare```

doug@doug-desktop:~/Desktop/GensForLinux$ CC=gcc-3.4 ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc-3.4
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc-3.4 accepts -g... yes
checking for gcc-3.4 option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc-3.4... gcc3
checking whether gcc-3.4 and cc understand -c and -o together... yes
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc-3.4 -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.4.0... yes (version 2.12.0)
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.1.3... yes
checking for nasm... /usr/bin/nasm
checking for clock_gettime in -lrt... yes
checking for getopt in -lc... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating pixmaps/Makefile
config.status: creating src/Makefile
config.status: creating src/gens/Makefile
config.status: creating src/starscream/Makefile
config.status: creating src/starscream/main68k/Makefile
config.status: creating src/starscream/sub68k/Makefile
config.status: creating config.h
config.status: executing default-1 commands
```

edit: It appears you can use checkinstall if you want to make a .deb
I didn't install from it but it looks ok - had to change the package version from 2.12 to something/anything? else - choose 1.12

---

### Post by GSZX1337 on 2008-02-09
> **mc4man said:**
> took a few tries (missing some packages)
```
CC=gcc-3.4 ./configure
```


I tried that and I'm still getting the same error.

---

### Post by mc4man on 2008-02-09
I don't have any experience with 64 bit - i know there's a -m32 option though i'm sure it's more complex than that - maybe having and linking to 32 bit libraries ect.
I think your best bet is to post over in development & programming > packageing and compiling

---

### Post by GSZX1337 on 2008-02-13
This post over in the main Gens thread has helped me out quite a bit. :)

> **roachk71 said:**
> I doubt there is a way to install a Debian package on Fedora, unless the Red Hat repositories offer dpkg and apt.

Although Ubuntu is a Debian-based distribution, the repos also include a tool for Red Hat packages to be converted into Debian packages (alien). I don't believe there's an easy way to do the reverse from Red Hat-based distributions, unfortunately.

However, if you manage to get your hands on the two packages mentioned above, you could download one of the 32-bit packages like I did (my machine is a dual-core AMD64-based one), and force its installation with:
```
dpkg --force-architecture -i *package_name*.deb
```Just make sure you have all of the 32-bit libraries needed by Gens installed first.

Uh, Oh: I just re-read that post, and it (as yet) has not been built for a PowerPC machine, so this could be dangerous to install on your hardware, or simply not work at all (without x86 emulation, that is.)

---

