---
title: "Installing Imagemagick"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-04-20
I'm trying to install Imagemagick
I downloaded a zip file , extracted it and ....
Not sure what to do....
I thought I'll go
```
./configure
make
make install
```
But after 'make' I just get a never ending string of code like this :
> if /bin/sh ./libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./magick -I./wand  -I./ltdl -I./ltdl    -g -O2 -Wall -pthread -MT magick/magick_libMagick_la-animate.lo -MD -MP -MF "magick/.deps/magick_libMagick_la-animate.Tpo" -c -o magick/magick_libMagick_la-animate.lo `test -f 'magick/animate.c' || echo './'`magick/animate.c; \
then mv -f "magick/.deps/magick_libMagick_la-animate.Tpo" "magick/.deps/magick_libMagick_la-animate.Plo"; else rm -f "magick/.deps/magick_libMagick_la-animate.Tpo"; exit 1; fi
What am I doing wrong?

---

### Post by derjames on 2006-04-20
Hey, you can install ImageMagik from Synaptic, I did that a couple of days ago... just mark it for installation and apply changes...

Cheers

---

### Post by seshomaru samma on 2006-04-21
Strange , according to synaptic I already have it.
But I can't find it anywhere.
I reinstalled it with synaptic ,but still can't find it....

---

### Post by halfvolle melk on 2006-04-21
Imagemagick is a set of tools/programs that can be run from command line:
[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)

You can add many options to those tools:
[http://www.imagemagick.org/script/command-line-options.php](http://www.imagemagick.org/script/command-line-options.php)

---

