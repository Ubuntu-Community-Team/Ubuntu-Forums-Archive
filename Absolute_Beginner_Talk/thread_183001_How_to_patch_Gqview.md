---
title: "How to patch Gqview"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by zAo on 2006-05-27
Hi there,

I want a thumbnailer for my Canon RAW files. I tried F-spot, but it is horrible slow. The 'new' Picasa is not opensource (like Bibble) and nothing more than a win32 program with libwine. The GUI is still win32.

I went to google and found this:
[http://www.y3m.net/docs/photography/code/gqview-2.1.0-dcraw.README](http://www.y3m.net/docs/photography/code/gqview-2.1.0-dcraw.README) 
It's a patch for Gqview. I tried Gqview on my JPG files and it was fast!

Can anyone please push me in the right direction, so that I can apply this patch?

Thanks in advance!

---

### Post by hw-tph on 2006-05-27
Download the source code matching the version of the patch (i.e. if the patch is for version 2.1.0 then download the 2.1.0 sources). Untar the source, apply the patch and then compile and install gqview.

*Edit:*
You will need to have a C/C++ development environment installed (compiler, C header files and so on). This is easily installed by typing **apt-get install build-essential**. You will also need xlibs-dev and at least libgtk2.0-dev packages, and most likely the dev packages for the different graphics formats.


Håkan

---

