---
title: "/usr/local/lib and /usr/lib"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by iamnafets on 2006-10-31
Ok, lets see.  I'm compiling amarok from scratch (latest release, MTP support, MusicBrainz, lots of stuff).  Anyways, I'm not having too much trouble except for dependencies, but...

On every library, it installs to /usr/local/lib

When I try to compile/configure another library (that depends on the first), it looks in /usr/lib.  Thus, usually I have to symbolically link the two (I don't know if that's right, but it works).  Anyways, I was curious if there was some global library search path that I could set (preferably persistently, so I don't have to redo it each restart), or some other way to compile where it puts the libraries in the right place.  Thanks in advance, you guys are awesome!

---

### Post by po0f on 2006-10-31
iamnafets,

Unless running `ldconfig` is part of the "make install" command for installing the library, your system doesn't know your custom-compiled libraries exist.  /usr/local/lib might not be in the library search path either.  Do the following as root:
```
# echo "/usr/local/lib" >> /etc/ld.so.conf
# ldconfig
```
The above command will append the directory /usr/local/lib to the /etc/ld.so.conf file, creating it if necessary.  ldconfig updates the system's cache on libraries installed.

Hope this helps.

---

