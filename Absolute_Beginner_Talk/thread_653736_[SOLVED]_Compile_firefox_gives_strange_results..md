---
title: "[SOLVED] Compile firefox gives strange results."
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by tmth on 2007-12-30
Hello.
Since firefox official downloads are only available in regular 32-bit version and i have a 64-bit Pentium D i thought i'd compile from source and apply the optimizations for my CPU. (-O3 -ffast-math) to get a version just for my platform.
Result is a an incredibly fast browser on startup and in usability!!

BUT instead of firefox i actually got Bon Echo (version 2.0.0.11 in help->about) which i find strange because i used latest stable firefox source file and from what i understand Bon Echo is code name for FF future developments. Is this what suppose to happen???

Next. No plugins(add-ons) are coming on. If i download "google tool bar" or "speed dial", when it restarts there are no plugins available. What could be wrong??

This is my .mozconfig:
. $topsrcdir/browser/config/mozconfig
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@
ac_add_options --enable-optimize="-O3 -ffast-math"
ac_add_options --enable-application=browser
ac_add_options --enable-system-cairo
ac_add_options --disable-debug 
ac_add_options --enable-default-toolkit=gtk2 
ac_add_options --enable-xft
ac_add_options --enable-static --disable-shared
ac_add_options --disable-libxul
ac_add_options --disable-tests

Thanks for any comments.

---

### Post by go_beep_yourself on 2007-12-30
```
sudo apt-get update
sudo apt-get build-dep firefox
sudo apt-get source -b firefox
```

---

### Post by tmth on 2007-12-30
That worked! Thanks.
Although it just don't feel right.  I guess its that .diff patch file that made the difference, and i don't know what all they did there and how beneficial or not those customizations are.
I'll still do some searching on why those plugins are not being activated the manual way.
I suspect it to be some permission problem and default location for extensions.  According to Mozilla, extensions go most often to /usr/lib(64)/firefox/extensions.  They never arrived there with Bon Echo thing but now they DO with ubuntu patches.

---

### Post by go_beep_yourself on 2007-12-31
> **tmth said:**
> That worked! Thanks.
Although it just don't feel right.  I guess its that .diff patch file that made the difference, and i don't know what all they did there and how beneficial or not those customizations are.
I'll still do some searching on why those plugins are not being activated the manual way.
I suspect it to be some permission problem and default location for extensions.  According to Mozilla, extensions go most often to /usr/lib(64)/firefox/extensions.  They never arrived there with Bon Echo thing but now they DO with ubuntu patches.

This thread is a bit old, but it might be useful to you.

[http://ubuntuforums.org/showthread.php?t=298553&highlight=compile+firefox](http://ubuntuforums.org/showthread.php?t=298553&highlight=compile+firefox)

---

