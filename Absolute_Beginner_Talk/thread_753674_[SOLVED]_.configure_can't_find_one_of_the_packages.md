---
title: "[SOLVED] ./configure can't find one of the packages"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Mark20 on 2008-04-13
Hi all,

I am trying to install something, I have unzipped my file, and tried using ./configure.
I then get the following error message:
```
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

This makes sense, because when I type whereis libgtk it tells me that is in /usr/lib/libgtk2.0-0.  Versus when I type whereis pkg-config, it tells me that the directory is usr/bin.  And I understand that this means that only packages in usr/bin will be detected.

What do I have to do to make it realize that I have gtk+-2.0 installed?
Is there any way that gtk+-2.0 is not the same package as libgtk2.0-0?

Thanks in advance!
Mark

---

### Post by Oldsoldier2003 on 2008-04-13
> **Mark20 said:**
> Hi all,

I am trying to install something, I have unzipped my file, and tried using ./configure.
I then get the following error message:
```
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

This makes sense, because when I type whereis libgtk it tells me that is in /usr/lib/libgtk2.0-0.  Versus when I type whereis pkg-config, it tells me that the directory is usr/bin.  And I understand that this means that only packages in usr/bin will be detected.

What do I have to do to make it realize that I have gtk+-2.0 installed?
Is there any way that gtk+-2.0 is not the same package as libgtk2.0-0?

Thanks in advance!
Mark

try installing libgtk2.0-dev I'm not 100% but I'm pretty sure that that should solve the issue

---

### Post by PinkFloyd102489 on 2008-04-13
Yeah usually when a configure script gives an error about missing dependencies, it's about -dev packages.

---

### Post by jw5801 on 2008-04-13
Also directories called "bin" are for binaries and ones called "lib" are for dynamically linked libraries. Thus, if libgtk is in /usr/lib/ and gtk is in /usr/bin/, the gtk+ package is installed to /usr/. The issue here is the absense of development packages, you need to install libgtk2.0-dev.

---

### Post by Mark20 on 2008-04-13
@ Oldsoldier2003
I downloaded the -dev package, tried my ./configure, and it worked perfectly!

@ jw5801
Everything works now, but I still find it strange that gtk doesn't seem to be in /usr/bin.
For example, if I go to the usr/bin directory, and type: ls | grep "gtk*" the following is returned:
```
ggtick
gtbl
gtf
gtk-builder-convert
gtk-query-immodules-2.0
gtk-update-icon-cache
jpegtran
ksvgtopng
pygtk-demo

```

I would have thought gtk, or gtk+-2.0 would have been there.  But neither of them are, which is confusing, but hey it works, so I can't complain

---

### Post by WW on 2008-04-13
gtk+ is a library. The package libgtk2.0-dev does install a few files in /usr/bin, but the majority are in /usr/lib and in /usr/include/gtk-2.0.  There is no gtk "program".

---

### Post by jw5801 on 2008-04-13
Yeah, as WW says, gtk is mostly a toolkit which supplies libraries for other programs to use, thus it doesn't really include a binary per se. However there are a few of those packages that are part of libgtk:
gtk-builder-convert
gtk-query-immodules-2.0
gtk-update-icon-cache

---

### Post by Mark20 on 2008-04-13
Ok, that makes sense.  I guess I still need to learn a bit more about the basics of how linux works.  Thanks!

---

