---
title: "ImageMagick Jpeg support"
date: 2011-06-20
forum: Art &amp; Design
---

### Post by gategatebodhisvaha on 2011-06-20
I've been trying to get imagemagick going, but can't seem to get the jpeg and other delegates to work. but when I make install or make make test, they all error. I've tried to remove imagemagick and re-install, with no luck.

Here's the sudo make install error:

make[1]: Entering directory `/home/daniel/imagemagick stuff/jpeg-8c'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ./libtool   --mode=install /usr/bin/install -c   libjpeg.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libjpeg.so.8.3.0 /usr/local/lib/libjpeg.so.8.3.0
libtool: install: (cd /usr/local/lib && { ln -s -f libjpeg.so.8.3.0 libjpeg.so.8 || { rm -f libjpeg.so.8 && ln -s libjpeg.so.8.3.0 libjpeg.so.8; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libjpeg.so.8.3.0 libjpeg.so || { rm -f libjpeg.so && ln -s libjpeg.so.8.3.0 libjpeg.so; }; })
libtool: install: /usr/bin/install -c .libs/libjpeg.lai /usr/local/lib/libjpeg.la
libtool: install: /usr/bin/install -c .libs/libjpeg.a /usr/local/lib/libjpeg.a
libtool: install: chmod 644 /usr/local/lib/libjpeg.a
libtool: install: ranlib /usr/local/lib/libjpeg.a
/bin/bash: /home/daniel/imagemagick: No such file or directory
make[1]: *** [install-libLTLIBRARIES] Error 127
make[1]: Leaving directory `/home/daniel/imagemagick stuff/jpeg-8c'
make: *** [install-am] Error 2

---

### Post by NovaAesa on 2011-06-20
Why don't you just use the imagemagic version that's in the repos? It works with jpeg just fine.

---

### Post by gategatebodhisvaha on 2011-06-21
Well, I was stupid and compiled it, before realising it was in repos. I thought I'd try to remove and re-install from repos, but it installs the same version, with the same problem. I've tried removing all connected dependencies I could find, and re-installing, a couple of times, but still same result.

---

### Post by gategatebodhisvaha on 2011-07-04
Okay, in case someone's done the same as me, and can't figure out how to get it from repositories. Go to the source, and do ./configure and then sudo make uninstall. Then you can install it with apt.

---

