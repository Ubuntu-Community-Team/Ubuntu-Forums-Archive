---
title: "Building a .deb"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by mlind on 2006-06-19
I debianized application called music-applet (successor of rhythmbox-applet)
which works okay, but I'd like to build debug package for it aswell.

I've added debug package info to debian/control
```

Package: music-applet-dbg
Architecture: any
Depends: music-applet (= ${Source-Version})
...

```

and debian/rules contains
```

DEB_DH_STRIP_ARGS += --dbg-package=music-applet-dbg

```

do I need to import some cdbs stuff in debinan/rules so I get debug package to
contain actual debug symbols?


/edit typo..

---

### Post by mlind on 2006-06-19
yes, I was missing cdbs imports.

---

