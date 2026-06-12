---
title: "Installing game"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Pray_II on 2007-02-24
Hi. Me again. Noob to the whole linux thing. I'm running Ubuntu 6.10 and recently started playing Sauerbraten on my windows machine. I see theres a Linux version so I was trying to install it in linux and I have come across a problem. I discovered i was missing some files so i went and got them. One of the files I was missing wont install because of the following error
> /usr/bin/ld: cannot find -lpng
collect2: ld returned 1 exit status
make: *** [libSDL_image.la] Error 1
any help on how to resolve this? I'm trying to install SDL_Image-1.2.5 and thats the error I get when i use the Make command.

---

### Post by po0f on 2007-02-24
Pray_II,

```
[font="Courier New"]$ sudo apt-get install libsdl-image1.2[/font]
```

There's no need to compile it, it's in the repos.

---

### Post by fre2rom on 2007-04-25
I tried what you had suggested below, but that did not resolve the problem either.

$ sudo apt-get install libsdl-image1.2


I have installed several packages which I've found to be dependencies for SDL.  I'm listing some of those below.  It's been a few years since I've used Linux.  I was hoping that there had been a major improvement in how software is installed.  I find it sad that when you attempt to install a game, the package still does not automatically install packages which are dependencies of the game's code.  With Windows ( I know, I said the W  word ), if your system does not already  have the framework ( Directx ) installed, the game gives you the option of installing the necessary framework.   Games and applications should work the same in Linux.  All dependencies should be taken care of by the package that you install.  

I've been using Linux since 1999 and have used several distros ( Red Hat, Mandrake, SUSE, Gentoo, etc ).  SDL is the toughest package to install that I've come across.  I've installed the packages below and SDL is still throwing the error below.  Do I have to run a command while facing west or do I need to say some special incantation in order to make SDL work?!

gcc -shared  .libs/IMG.o .libs/IMG_bmp.o .libs/IMG_gif.o .libs/IMG_jpg.o .libs/IMG_lbm.o .libs/IMG_pcx.o .libs/IMG_png.o .libs/IMG_pnm.o .libs/IMG_tga.o .libs/IMG_tif.o .libs/IMG_xcf.o .libs/IMG_xpm.o .libs/IMG_xv.o  -Wl,--rpath -Wl,/usr/local/lib -Wl,--rpath -Wl,/usr/local/lib -lpng -lz -L/usr/local/lib /usr/local/lib/libSDL.so -lpthread  -Wl,-rpath -Wl,/usr/local/lib -Wl,-soname -Wl,libSDL_image-1.2.so.0 -o .libs/libSDL_image-1.2.so.0.1.4
/usr/bin/ld: cannot find -lpng
collect2: ld returned 1 exit status
make: *** [libSDL_image.la] Error 1


---------------------------------------------------------------------------------------

libvorbis-dev_1.1.2-1ubuntu1_i386.deb
libogg-dev_1.1.3-2ubuntu1_i386.deb
libogg0_1.1.3-2ubuntu1_i386.deb
libvorbis0a_1.1.2-1ubuntu1_i386.deb
libvorbisenc2_1.1.2-1ubuntu1_i386.deb
libvorbisfile3_1.1.2-1ubuntu1_i386.deb
 libjpeg62-dev_6b-13_i386.deb
libtiff4-dev_3.8.2-7_i386.deb
libtiffxx0c2_3.8.2-7_i386.deb
zlib1g-dev_1.2.3-13_i386.deb
zlib1g_1.2.3-13_i386.deb
libtiff4_3.8.2-7_i386.deb
libpng-1.2.16-i486-1.tgz
libc6_2.4-1ubuntu12.3_i386.deb

---

