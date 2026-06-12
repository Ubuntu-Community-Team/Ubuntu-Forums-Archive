---
title: "Svgalib compilng error"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2007-05-20
Svgalib install does not work, Its off a magazine dvd and im not sure how to go about installing it.
it says that it should already have a precompiled 'a' file, and that sudo make install should work. It comes up with the following


 -o vga.o /svgalib-1.4.3/src/vga.c
/svgalib-1.4.3/src/vga.c:3919:1: error: pasting "." and "HDisplay" does not give a valid preprocessing token
/svgalib-1.4.3/src/vga.c:3920:1: error: pasting "." and "HSyncStart" does not give a valid preprocessing token
/svgalib-1.4.3/src/vga.c:3921:1: error: pasting "." and "HSyncEnd" does not give a valid preprocessing token
/svgalib-1.4.3/src/vga.c:3922:1: error: pasting "." and "HTotal" does not give a valid preprocessing token
/svgalib-1.4.3/src/vga.c:3923:1: error: pasting "." and "VDisplay" does not give a valid preprocessing token
/svgalib-1.4.3/src/vga.c:3924:1: error: pasting "." and "VSyncStart" does not give a valid preprocessing token
/svgalib-1.4.3/src/vga.c:3925:1: error: pasting "." and "VSyncEnd" does not give a valid preprocessing token
/svgalib-1.4.3/src/vga.c:3926:1: error: pasting "." and "VTotal" does not give a valid preprocessing token
make[1]: *** [vga.o] Error 1
make[1]: Leaving directory `/svgalib-1.4.3/sharedlib'
make: *** [sharedlib/libvga.so.1.4.3] Error 2
bellinator@Alture:/svgalib-1.4.3$ c

---

### Post by Belliinator on 2007-05-20
A little help please

---

### Post by matrixcosmos on 2008-01-12
I also get this problem, Help us!

---

### Post by geirha on 2008-01-12
Could you post all commands you've run since downloading the source code? so it's easy to reproduce it on our end. 

And, any reason why you need to compile svgalib yourself, instead of using the one in the ubuntu repositories? (package is called libsvga1, and if you need to compile something that uses the lib, you'll also need libsvga1-dev)

---

### Post by dstew on 2008-01-12
Do you have the package **build-essential** installed? If you are compiling from source, this is necessary. You might also need **linux-headers** for your particular kernel.

However, it is much easier to install the svgalib package from Synaptic, as mentioned by geirha. I think the package you want is svgalib-bin in the Graphics (universe) repository.

---

