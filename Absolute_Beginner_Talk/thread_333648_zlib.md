---
title: "zlib"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by son365 on 2007-01-07
O/S: Ubuntu 6.06 (Dapper Drake)

I am attempting to install PostgreSQL 8.2 from source, and when I run its configure script, it outputs the following error:

"configure: error: zlib library not found
If you have zlib already installed, see config.log for details on the
failure.  It is possible the compiler isn't looking in the proper directory."

From what I can tell, Dapper already has this library:
"desktop:/$ dpkg -l | grep zlib
ii  zlib1g                                 1.2.3-6ubuntu4                         compression library - runtime"

However, I cannot find any zlib header files, and the only zlib library I can see is "/usr/lib/python2.4/lib-dynload/zlib.so".

I've already tried running the following:
- "$ ./configure --with-PACKAGE=zlib1g" ---> it outputs the same error.
- searched the config.log for the directory it is using to find the library ---> I could not find anything.

Any ideas/recommendations?  I've thought of manually installing the zlib library, but I'm concerned that this may not be necessary and/or may interfere with zlib1g 1.2.3-6ubuntu4 that comes with Ubuntu 6.06.

Ubuntu 6.06 is my first attempt at using linux, and this is my first post on a linux forum.  Any help would be appreciated.

---

### Post by Jussi Kukkonen on 2007-01-07
Since you said you're new I'll warn you first: what you are doing is usually a bad idea. The reason it takes some time for complex packages like postgres to come in to Debian (and Ubuntu) is that packaging/installing them is not always trivial. Also, installing stuff from non-debianized source breaks the package management.

If you still want to go ahead: Nothing guarantees this helps, but a good start in these cases is always to install the build prerequisites for the previous version (the one in repositories):
```
apt-get build-dep postgresql

```
you might need other packages too, but that's a start.

your configure flags might be wrong, btw: It would sound more correct like this *./configure --with-zlib=/path/to/zlib* but that should be explained in either INSTALL-file or "./configure --help"

---

### Post by po0f on 2007-01-07
son365,

[zlib1g-dev](http://packages.ubuntu.com/edgy/libdevel/zlib1g-dev) is in the repos, how hard did you look?  ;)

[EDIT]

The above link is for Edgy, I just noticed you said you were using Dapper.  The package name is the same regardless, just:
```
[font="Courier New"]$ sudo aptitude update && sudo aptitude install zlib1g-dev[/font]
```

---

### Post by son365 on 2007-01-09
poOf:
"Not hard enough." to answer your question.  Thanks so much; it was smooth sailing after having installed zlib1g-dev.

Jussi:
I appreciate the swift response.  I was shocked to see how soon after I made a post that somebody answered.

both:
Again, many thanks.  I've enjoyed this experience.  I look forward to when I'll be proficient enough in linux/ubuntu, to be able lend assistance on this forum to upcoming newbs like myself.

Cheers and success to you both.

---

