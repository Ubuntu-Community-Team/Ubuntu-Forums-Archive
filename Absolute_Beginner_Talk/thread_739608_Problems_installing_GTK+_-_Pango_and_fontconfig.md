---
title: "Problems installing GTK+ - Pango and fontconfig"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by eljaydub on 2008-03-29
I"m having trouble getting gtk+ installed on my gutsy. It seems the problem is of course with all the dependencies involved. Currently I am trying to get Pango working but if gives me this error when i run configure:

checking for perl... perl
checking for X... no
configure: WARNING: X development libraries not found
checking for pkg-config... /usr/local/bin/pkg-config
checking for fontconfig >= 1.0.1... configure: WARNING: No fontconfig found, skipping tests for FreeType and Xft
configure: error: *** Didn't find any of FreeType, X11, or Win32.
*** Must have at least one backend to build Pango.


I do have Freetype installed so I figured the problem was fontconfig. Now I get the following problem when running make on fontconfig:

fcfreetype.c:2747: warning: nested extern declaration of 'FT_MEM_ALLOC_ARRAY'
fcfreetype.c:2747: error: expected expression before 'FT_ULong'
fcfreetype.c:2756: warning: implicit declaration of function 'FT_GET_ULONG'
fcfreetype.c:2756: warning: nested extern declaration of 'FT_GET_ULONG'
fcfreetype.c:2787: warning: implicit declaration of function 'FT_FREE'
fcfreetype.c:2787: warning: nested extern declaration of 'FT_FREE'
fcfreetype.c:2714: warning: unused variable 'memory'
fcfreetype.c: In function 'FcFontCapabilities':
fcfreetype.c:2823: warning: pointer targets in passing argument 1 of 'strcpy' differ in signedness
fcfreetype.c:2800: warning: unused variable 'memory'
make[2]: *** [fcfreetype.lo] Error 1
make[2]: Leaving directory `/home/eljaydub/Desktop/fontconfig-2.3.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/eljaydub/Desktop/fontconfig-2.3.2'
make: *** [all] Error 2

Does anyone know what to do to fix this?
Is there an easier way to install gtk+? (I also tried the XMMS method but still no luck)

Thanks

---

### Post by scragar on 2008-03-29
isn't pango and GTK installed by default?

if you after the development packages:
```
sudo apt-get install libpango1.0-dev libgtk2.0-dev
```

---

### Post by eljaydub on 2008-03-29
The ultimate goal was to get DC++ and some openGL apps to run but I just ran the code you supplied and still I get this error when I try to install DC++ with scons:

scons: Reading SConscript files ...
Checking for g++ >= 3.4...(cached) yes
Checking for pkg-config... yes
Checking for gtk+-2.0 >= 2.6... no
        gtk+ >= 2.6 not found.
        Note: You might have the lib but not the headers

Thanks for the code though

---

### Post by scragar on 2008-03-29
[http://packages.ubuntu.com/gutsy/libgtk2.0-dev](http://packages.ubuntu.com/gutsy/libgtk2.0-dev) <-- gutsy has 2.12.0 what are you running(because the gutsy one is good enough...)?

---

### Post by eljaydub on 2008-03-29
I'm running Gutsy, freshly installed 2 weeks ago, so you're right I should have it. So the question is how come DC++ doesn't think I do?

---

### Post by scragar on 2008-03-29
no idea, maybe try:
```
sudo apt-get build-dep libpango1.0 libgtk2.0
```
but I've not checked that command(should work though)

---

### Post by eljaydub on 2008-03-30
Here's what I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for libpango1.0


Maybe it's the wrong name for the pango package? Thanks for the help!

---

