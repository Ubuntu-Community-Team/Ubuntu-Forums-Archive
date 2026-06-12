---
title: "Compiling Under Ubuntu 6.06"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by tin2 on 2006-12-04
This Output comes when i put 

   ./configure --datadir=/usr/share/games/wesnoth/
  

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
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
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for ranlib... ranlib
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries /usr/X11R6/lib, headers
checking whether -R must be followed by a space... neither works
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XOpenDisplay in -lX11... yes
checking for sdl-config... /usr/bin/sdl-config
checking for fribidi-config... no
configure: WARNING: *** FRIBIDI not found.
checking for libpng-config... no
checking for libpng12-config... no
checking for pkg-config... /usr/bin/pkg-config
Package libpng12 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpng12.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libpng12' found
Package libpng12 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpng12.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libpng12' found
checking for SDL - version >= 1.2.7... yes
checking for gnome-config... no
checking for kde-config... /usr/bin/kde-config
checking for libtool... /usr/bin/libtool
checking for IMG_Load in -lSDL_image... no
configure: error: *** SDL_image lib not found! Get SDL_image from
[http://www.libsdl.org/projects/SDL_image/index.html](http://www.libsdl.org/projects/SDL_image/index.html)

What do you think?
I use kubuntu 6.06

---

### Post by aysiu on 2006-12-04
Anything wrong with using the package manager to install *wesnoth*?

**Step 1**: Enable extra repositories
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2**: Paste this command into the terminal ```
sudo aptitude update && sudo aptitude install wesnoth
``` More on installing software here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by po0f on 2006-12-04
tin2,

Quick answer: install [libsdl-image1.2-dev](http://packages.ubuntu.com/dapper/libdevel/libsdl-image1.2-dev).

Long answer: whenever you compile packages from source, you will need to look through the README (I know, who reads those things anymore?) to see what are the prerequisites for installing the software.  You will need the libraries mentioned, as well as the associated *-dev packages to get the header files needed for compilation of custom software.

Ubuntu (and all the other binary distributions) install *just* the library when you go to install libfoo, because everything is already compiled for you, no need for the header files.  This may be slightly confusing to new people, because they think they do have the dependencies satisfied (I just installed libfoo!).

In Ubuntu-land, you can get the header files for a library libfoo by installing libfoo-dev, just in case you want to install other header files as well.

[EDIT]

Or you can follow aysiu's advice posted above, I didn't even realize that the package in question was Wesnoth, I just scrolled straight down to the error.  ;)

---

### Post by Sef on 2006-12-04
Read [How to Install Anything]("read How to Install Anything in Ubuntu.") in Ubuntu for a pictorial tutorial on installing software in Ubuntu.

---

### Post by aysiu on 2006-12-04
> **Sef said:**
> Read [How to Install Anything]("read How to Install Anything in Ubuntu.") in Ubuntu for a pictorial tutorial on installing software in Ubuntu.
I'm not sure that applies directly to Kubuntu.

---

### Post by tin2 on 2006-12-04
it brought out another error.
I checked the prerequisites in its site.
I did install all of them.
It went fine in ubuntu but it is not so well now .. in kubuntu.
Is there any binary package for this? (the latest version)

---

### Post by tin2 on 2006-12-04
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
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
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for ranlib... ranlib
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries /usr/X11R6/lib, headers
checking whether -R must be followed by a space... neither works
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XOpenDisplay in -lX11... yes
checking for sdl-config... /usr/bin/sdl-config
checking for fribidi-config... no
configure: WARNING: *** FRIBIDI not found.
checking for libpng-config... /usr/bin/libpng-config
checking for SDL - version >= 1.2.7... yes
checking for gnome-config... no
checking for kde-config... /usr/bin/kde-config
checking for libtool... /usr/bin/libtool
checking for IMG_Load in -lSDL_image... yes
checking for Mix_OpenAudio in -lSDL_mixer... yes
checking for SDLNet_Init in -lSDL_net... no
configure: error: *** SDL_net lib not found! Get SDL_net from
[http://www.libsdl.org/projects/SDL_net/index.html](http://www.libsdl.org/projects/SDL_net/index.html)

now?

---

### Post by aysiu on 2006-12-04
> **tin2 said:**
> now? Read post #2 of this thread.

---

### Post by tin2 on 2006-12-04
My Bandwith is very expensive... I will rather try the other way

---

### Post by tin2 on 2006-12-04
Anyone?

---

### Post by kakalaky on 2006-12-04
```
sudo apt-get install libsdl-net1.2-dev
```

---

