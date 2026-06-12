---
title: "Libtool install"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-01-19
Ok...another problem....I get this error --configure: error: Cannot find ltdl.h -- libtool-devel (or libtool-ltdl-devel) not installed?  Where do I find libtool to install.  I can't seem to find it.
Thanks again..and again ; )

---

### Post by po0f on 2007-01-19
MrKlean,

First, to install libtool, just run `sudo aptitude install libtool`.  Second, to get that file, install [libltdl3-dev](http://packages.ubuntu.com/edgy/libdevel/libltdl3-dev) as well:
```
[FONT="Courier New"]$ sudo aptitude update
$ sudo aptitude install libtool libltdl3-dev[/FONT]
```

---

### Post by MrKlean on 2007-01-19
Thank you poOF  : )

---

### Post by MrKlean on 2007-01-19
Each step takes me closer away !!      LOL!!

---

