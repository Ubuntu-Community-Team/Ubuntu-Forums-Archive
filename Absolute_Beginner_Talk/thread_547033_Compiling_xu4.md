---
title: "Compiling xu4"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Atomic Paperclip on 2007-09-09
I'm trying to make [xu4]("http://xu4.sourceforge.net/") under 7.04 and this is what I get:

g++ -DHAVE_BACKTRACE=1 -DHAVE_VARIADIC_MACROS=1 -Wall -I. -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/libxml2 -DICON_FILE=\"/usr/local/share/pixmaps/u4.bmp\" -DVERSION=\"1.0beta3\" -ggdb1 -rdynamic   -c -o codex.o codex.cpp
imagemgr.h:105: error: extra qualification ‘ImageMgr::’ on member ‘getSubImage’
make: *** [codex.o] Error 1

What am I missing here? I thought I installed all the right packages to get this to work.

---

### Post by Linux_Man on 2007-09-09
You have the build-essential package installed right? And your following the readme for the program your installing?

---

### Post by Atomic Paperclip on 2007-09-09
I did not have build-essential installed. I installed it and got the same error.

Here is the instructions from the readme:

COMPILING
---------

Note that you need libxml2, SDL, the SDL development libraries &
headers, and the SDL_mixer library to compile.  TiMidity++ may be
necessary on some platforms, too.  Assuming they are present, type
make in the src directory to build it.  An executable called u4 is
created.

I had to guess at these packages, especially the SDL ones. If someone knows the exact names in 7.04, that would be great.

---

### Post by Perfect Storm on 2007-09-09
Just tried it with all libs, still same error happens to me too;

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential libsdl1.2-dev libsdl-mixer1.2-dev libxml2-dev


Another way around would be alien the .rpm package though there aren't any gurantee it will work.

---

### Post by Perfect Storm on 2007-09-09
This is not recommended - Do not use this with important libs or other system stuff - installing .rpm package from another distro (and then converting them) can break your system.

I have tested this for you so go ahead :)

Download the binary .rpm package to your Desktop;

```

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install alien
cd ~/Desktop
sudo alien -i xu4-1.0beta3-1.i386.rpm
u4

```

---

### Post by Atomic Paperclip on 2007-09-10
Thanks, using alien allowed it to install.

Xu4 has other problems while running. Looks like a trip back to sourceforge now for me.

---

