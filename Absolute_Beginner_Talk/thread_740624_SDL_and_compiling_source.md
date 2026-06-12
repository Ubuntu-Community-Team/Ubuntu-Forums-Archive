---
title: "SDL and compiling source"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2008-03-30
I know how to install packages through synaptic. Openglad just isnt availabile as far as I know from a .deb package. etc When I try to configure the system for install, it complains SDL is missing. As far as I can tell, its already installed. Any ideas?

```
bellinator@bellpoint:~/openglad/openglad-0.98$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!

```

An installed package in synaptic listed as libsdl1.2debain is installed.
This is not the first compiled program to recieve this error. Any help?

---

### Post by zvacet on 2008-03-31
Install** libsdl1.2-dev** and if that doesn´t help ** libsdl-image1.2** and **libsdl-image1.2-dev**.

---

### Post by Belliinator on 2008-03-31
Ok I needed to download libsdl1.2-dev to compile it. So now Im up to the next stage in compiling. Im just working through that now

---

### Post by Belliinator on 2008-03-31
I have an error like this when in make
```
URCE=1 -D_REENTRANT -c -o util.o `test -f util.cpp || echo './'`util.cpp
g++  -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -o openglad
.o button.o effect.o game.o gladpack.o graphlib.o guy.o help.o input.o intro.o living.o loader.o obmap.o pal32.o parser.o picker.o pixie.o pixien.o radar.o screen.o smooth.o sound.o stats.o text.o treasure.o video.o view.o walker.o weap.o sai2x.o util.o  -L/usr/lib -lSDL
sound.o: In function `soundob::play_sound(short)':
/home/bellinator/openglad/openglad-0.98/src/sound.cpp:158: undefined reference to `Mix_PlayChannelTimed'
sound.o: In function `soundob::load_sound(Mix_Chunk**, char*)':
/home/bellinator/openglad/openglad-0.98/src/sound.cpp:122: undefined reference to `Mix_LoadWAV_RW'
sound.o: In function `soundob::init()':
/home/bellinator/openglad/openglad-0.98/src/sound.cpp:72: undefined reference to `Mix_OpenAudio'
/home/bellinator/openglad/openglad-0.98/src/sound.cpp:78: undefined reference to `Mix_AllocateChannels'
sound.o: In function `soundob::free_sound(Mix_Chunk**)':
/home/bellinator/openglad/openglad-0.98/src/sound.cpp:135: undefined reference to `Mix_FreeChunk'
sound.o: In function `soundob::shutdown()':
/home/bellinator/openglad/openglad-0.98/src/sound.cpp:150: undefined reference to `Mix_CloseAudio'
sound.o: In function `soundob::load_sound(Mix_Chunk**, char*)':
/home/bellinator/openglad/openglad-0.98/src/sound.cpp:130: undefined reference to `Mix_VolumeChunk'
collect2: ld returned 1 exit status
make[2]: *** [openglad] Error 1
make[2]: Leaving directory `/home/bellinator/openglad/openglad-0.98/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/bellinator/openglad/openglad-0.98/src'
make: *** [all-recursive] Error 1

```

---

### Post by zvacet on 2008-04-01
Look [here](http://freshmeat.net/projects/openglad/) and see do you have all dependencies installed.

---

