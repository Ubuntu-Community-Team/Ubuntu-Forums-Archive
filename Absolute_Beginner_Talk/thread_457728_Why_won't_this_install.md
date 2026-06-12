---
title: "Why won't this install?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by je1117 on 2007-05-28
I am trying to compile SDL, and everything is peachy until sudo make install (or in my case sudo checkinstall -D). This is what it outputs at the end.

/usr/bin/install -c -m 644 build/libSDLmain.a /usr/local/lib/libSDLmain.a
ranlib /usr/local/lib/libSDLmain.a
/bin/bash ./build-scripts/mkinstalldirs /usr/local/share/aclocal
/usr/bin/install -c -m 644 ./sdl.m4 /usr/local/share/aclocal/sdl.m4
/bin/bash ./build-scripts/mkinstalldirs /usr/local/lib/pkgconfig
/usr/bin/install -c -m 644 ./sdl.pc /usr/local/lib/pkgconfig
/bin/bash ./build-scripts/mkinstalldirs /usr/local/man/man3
mkdir -p -- /usr/local/man/man3
mkdir: cannot create directory `/usr/local/man': File exists
make: *** [install-man] Error 1

Thank yous are given in advance.

---

### Post by dunedust on 2007-05-29
It says that you don't have permission to make a directory
Thats probably because you are not logged in as root
Log in as root in the terminal and then follow the installation steps

To login as root 

```
sudo -s 
```

---

### Post by je1117 on 2007-05-30
That wasn't it. Same message. I have no idea what the output means. HELP. (Please.)

---

