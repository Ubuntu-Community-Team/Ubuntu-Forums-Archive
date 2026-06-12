---
title: "ZSNES emulator?"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by KevNice on 2006-04-19
Hi, Im trying to install an emulator, and I was wondering if anyone had experience with this particular program. Anyway, I downloaded the tar.gz file, and I went to configure it, and I get this text: 

kevin@softbank221079077024:~/Desktop/zsnes_1_42/src$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for a BSD-compatible install... /usr/bin/install -c
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: SDL >= 1.2.0 is required


I don't know what that file is... the readme says:
 You need:
DJGPP v2 or higher, (GCC also installed) : [http://www.delorie.com/djgpp/](http://www.delorie.com/djgpp/)
                   using the zip picker, the default choices are ok if you
                   check C and C++ in the programming languages. You also need 
                   to get zlib which is available with the full distribution 
                   of djgpp. You can get it at :
                   [ftp://ftp.simtel.net/pub/simtelnet/gnu/djgpp/v2tk/zlib112b.zip](ftp://ftp.simtel.net/pub/simtelnet/gnu/djgpp/v2tk/zlib112b.zip)

then it starts talking about cross compiling and I get lost. Anyone have any experience with this program?

---

### Post by zugu on 2006-04-19
You could try this:

apt-get install zsnes

rather than compiling from the sources. Don't forget to enable multiverse before.

---

### Post by croak77 on 2006-04-19
If you still want to compile zsnes then you need all the dependencies. You  error says you're missing SDL. Try installing  libsdl1.2-dev.

---

### Post by auroraborealis on 2006-04-19
Or get your all dependencies by doing

apt-get build-dep zsnes

---

### Post by yellow beard on 2006-05-03
I got it working fine, but the mouse is lagging really bad. Do you know what can cause this/how to fix?

---

### Post by shutupimpoor on 2006-05-07
[QUOTE=auroraborealis]Or get your all dependencies by doing

apt-get build-dep zsnes[/QUOTE]

that doesn't work for me?

---

### Post by shutupimpoor on 2006-05-07
i just used apt-cache nasm and installed from that. thanks anyway

---

