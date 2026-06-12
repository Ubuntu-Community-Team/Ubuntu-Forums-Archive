---
title: "Trying to install glc"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Faud on 2007-11-15
Im at this part ( on screenshot ) and have no idea what this stuff means or what option to choose

---

### Post by kpkeerthi on 2007-11-15
I can help. But you need to tell me what processor you have? (Pentium 4 or celeron or Pentium-M)

---

### Post by Faud on 2007-11-15
it says intel pentium (R) D cpu 2.80

---

### Post by kpkeerthi on 2007-11-15
Or just visit [http://www.getswiftfox.com/releases.htm](http://www.getswiftfox.com/releases.htm). Click on the processor link as appropriate and you can see the optimizations available.

---

### Post by Faud on 2007-11-15
Thank you for the link...so my processer is   Celeron (Willamette, Northwood, Celeron D) ?

---

### Post by kpkeerthi on 2007-11-15
For pentium D specific optimization, enter 
```

-march=prescott -O2 -pipe -fomit-frame-pointer

```

If you do not prefer any compiler specific optimization (ubuntu default), you can just enter
```

-march=i386 -O2 -pipe -fomit-frame-pointer

```

For more information, see [http://gentoo-wiki.com/Safe_Cflags](http://gentoo-wiki.com/Safe_Cflags)

---

### Post by Faud on 2007-11-15
Attached is my error,

```

ryan@ryan-desktop:~$ ./glc-build.sh
info  : Welcome to glc install script!
        Enter path where glc will be installed.
          (leave blank to install to root directory)
      > /home
        Enter compiler optimizations.
          (-O2 -msse -mmmx -fomit-frame-pointer -mtune=pentium3)
      > -march=prescott
        Enter linker optimizations. (-Wl,-O1)
      > -O2
info  : Fetching sources...
info  : Unpacking sources...
info  : Building elfhacks...
info  : Building packetstream...
info  : Building glc...
src/stream/gl_capture.c:18:38: error: X11/extensions/xf86vmode.h: No such file or directory
src/stream/gl_capture.c: In function ‘gl_capture_update_color’:
src/stream/gl_capture.c:687: error: ‘XF86VidModeGamma’ undeclared (first use in this function)
src/stream/gl_capture.c:687: error: (Each undeclared identifier is reported only once
src/stream/gl_capture.c:687: error: for each function it appears in.)
src/stream/gl_capture.c:687: error: expected ‘;’ before ‘gamma’
src/stream/gl_capture.c:690: error: ‘gamma’ undeclared (first use in this function)
make: *** [build/gl_capture.o] Error 1
error : Can't compile glc

```

---

### Post by Faud on 2007-11-15
Any ideas on where the error is coming from ?

---

