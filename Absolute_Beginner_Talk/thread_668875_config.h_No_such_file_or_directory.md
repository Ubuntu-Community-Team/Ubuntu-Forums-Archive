---
title: "config.h: No such file or directory"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by yipeskop on 2008-01-15
I am trying to install aegisub but when a do the "make" command I get an error saying
```
auto4_base.cpp:36:20: error: config.h: No such file or directory
```

anyone know how to fix this? :confused:

(I am using Ubuntu 7.0 64bit version and I have installed linux-header-`uname -r` already)

---

### Post by PeterJS on 2008-01-15
Have you read the README/INSTALL file? have you run ./configure?

---

### Post by zvacet on 2008-01-16
Did you follow [this instructions](http://malakith.net/aegiwiki/Unix_Instructions)?

---

### Post by yipeskop on 2008-01-16
yes I followed all the instructions and installed all the prerequisites via synaptic already. but when using the "make" command I get the error about config.h

---

### Post by zvacet on 2008-01-17
First of all go to the folder in wich you are compiling and 

```
sudo make clean
```

That will clean all your work in that folder wich is good,because you can start fresh.Start with this command

```
auto-apt run ./configure
```

if all goes well you can after that run **make** command.When it is finish

```
sudo make install
```

---

### Post by PeterJS on 2008-01-17
> **zvacet said:**
> 
```
auto-apt run ./configure
```


I did not know about that, that is an awesome tool. Makes installing from source so much easier.

---

### Post by Omnios on 2008-01-17
config.h is probably a file that the .config is supposed to generate. 
This can possibly be caused by config now being able to write to the file or a broken tarball. Its been so long since I build a tarball that I forget lol.

---

### Post by yipeskop on 2008-01-18
> **zvacet said:**
> First of all go to the folder in wich you are compiling and 

```
sudo make clean
```

That will clean all your work in that folder wich is good,because you can start fresh.Start with this command

```
auto-apt run ./configure
```

if all goes well you can after that run **make** command.When it is finish

```
sudo make install
```

I still get the same error :(

---

### Post by yipeskop on 2008-01-23
bump

---

### Post by yipeskop on 2008-01-25
well I tried reinstalling it by deleting everything and going through the installation steps again on the wiki but now I get a slightly new error,

```
In file included from ./posix/defines.h:19,
                 from <command line>:1:
./stdwx.h:58:20: error: config.h: No such file or directory
In file included from ./posix/defines.h:19,
                 from <command line>:1:
./stdwx.h:63: warning: ignoring #pragma warning 
In file included from ./posix/defines.h:19,
                 from <command line>:1:
./stdwx.h:102: warning: ignoring #pragma warning 
In file included from <command line>:1:
./posix/defines.h:30:1: error: posix/config.h: No such file or directory
```

still about config.h but now it says something about posix.

---

### Post by kozec on 2008-02-10
I resolved this problem with [these]("http://en.alanny.ru/2008/01/aegisub-under-linux.html") instructions, and created posix/config.h with following content```
#pragma once
#ifndef BUILD_CREDIT
#define BUILD_CREDIT "Anonymous"
#endif
#define WITH_AUTOMATION
#define WITH_FREETYPE2
//#define WITH_HUNSPELL
#define WITH_OLD_HUNSPELL
//#define WITH_PERL
#define WITH_FONTCONFIG
#define WITH_LIBASS
#define WITH_FFMPEG
//#define WITH_RUBY
#define WITH_PORTAUDIO
//#define WITH_ALSA
//#define WITH_OPENAL
#define WITH_PULSEAUDIO
```and modifiing Makefile.am to this```
AUTOMAKE_OPTIONS = foreign
SUBDIRS = ac automation csri aegisub po
ACLOCAL_AMFLAGS = -I m4
```. Then I compiled csri by hand (because normal make refused to do it, dony ask me why)```
cd csri
./bootstrap
./configure
make
```and now i'am getting *error: lua.hpp: No such file or directory* error :( Where can I find lua.hpp?

edit: After solving previsious and another 7 errors i recieved *video_provider_lavc.cpp:48:28: error: ffmpeg/swscale.h: No such file or directory* and i'am gived it up :(

---

### Post by yipeskop on 2008-02-10
even after making the config.h file in aegisub/posix It still says that config.h is missing :(

---

### Post by Light- on 2008-03-01
I'm encountering the same error

I asked around in the aegisub IRC channel, and apparently linux support has been broken again, and they've got someone working on fixing it.

---

