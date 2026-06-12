---
title: "[SOLVED] Rutilt0.15 compiling help"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by neu_ser on 2007-10-29
I am attempting to install rutilt and I'm struggling to satisfy the dependencies.

I seem to get errors no matter what:
```
neu@ser:~/Desktop/rt61driver/RutilTv0.15$ ./configure.sh
./configure.sh: 139: pkg-config: not found
Please install (or upgrade to) GTK+ 2.6.0, at least.
```

I found [this]("http://ubuntuforums.org/showthread.php?t=554089") thread and fired up Adept Package Manager. I found and installed g++-4.1 but could not find libgtk2.0-dev there.
I searched this site and downloaded libglib2.0-dev_2.10.2-1ubuntu3_i386.deb.
On trying to install this it complains about yet another dependency not satisfied: libglib2.0-0.
I repeated the above and downloaded libglib2.0-0_2.14.1-1ubuntu1_i386.deb from a mirror.
I install this but libglib2.0-dev still complains about the dependency.

Any help is appreciated of where I'm going wrong here.

---

### Post by testube_babies on 2007-10-29
EDIT:  rutilt is in the Universe repository.  Make sure you have that repo enabled and you can install it via adept.
[http://packages.ubuntu.com/gutsy/net/rutilt](http://packages.ubuntu.com/gutsy/net/rutilt)

---

### Post by neu_ser on 2007-10-29
> **testube_babies said:**
> EDIT:  rutilt is in the Universe repository.  Make sure you have that repo enabled and you can install it via adept.
[http://packages.ubuntu.com/gutsy/net/rutilt](http://packages.ubuntu.com/gutsy/net/rutilt)

That worked a treat. Thanks.

---

