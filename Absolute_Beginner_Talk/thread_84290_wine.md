---
title: "wine"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by brykn on 2005-10-30
Hello,
I was installing wine 9.0 and ran into a problem.  

gcc -c -I. -I. -I../../include -I../../include -I/usr/X11R6/include -D__WINESRC__   -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2  -o bitblt.o bitblt.c
bitblt.c:27:27: X11/Intrinsic.h: No such file or directory
bitblt.c: In function `BITBLT_InternalStretchBlt':
bitblt.c:1334: error: `pixel' undeclared (first use in this function)
bitblt.c:1334: error: (Each undeclared identifier is reported only once
bitblt.c:1334: error: for each function it appears in.)
bitblt.c:1334: error: syntax error before "xor_pix"
bitblt.c:1337: error: `xor_pix' undeclared (first use in this function)
make[2]: *** [bitblt.o] Error 1
make[2]: Leaving directory `/home/kyle/wine-0.9/dlls/x11drv'
make[1]: *** [x11drv] Error 2
make[1]: Leaving directory `/home/kyle/wine-0.9/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

Can anyone help me?
thank you for your time.

---

### Post by Remmelas on 2005-10-30
I'm unsure if you have a specific reason to install this from source, but, if you want to get up and running fast on the latest release of wine, add the following line to your /etc/apt/sources.list

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

then, sudo apt-get update
then, apt-get install wine

will have u running pretty quick.  If you really do want to install it from source, i'm afraid I'm not much help there, except that it doesn't look like your x11 development libraries are installed, which would be required to compile wine from source.  I'm unsure of an easy way to find what package Intrinsic.h (your missing file) belongs to however.

---

