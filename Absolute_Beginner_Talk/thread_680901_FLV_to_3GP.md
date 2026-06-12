---
title: "FLV to 3GP"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by auraithx on 2008-01-28
Following this guide

[http://mapopa.blogspot.com/2007/03/converting-3gp-movies-to-flv-in-ubuntu.html](http://mapopa.blogspot.com/2007/03/converting-3gp-movies-to-flv-in-ubuntu.html)

I get stuck here
```
./configure --prefix=/opt/ffmpeg --enable-amr_nb --enable-amr_wb --enable-libogg --enable-libvorbis --enable-libgsm --enable-xvid --enable-liba52 --enable-libmp3lame --enable-gpl
```

this is the error I get

```
root@mark-desktop:/home/mark/ffmpeg# ./configure --prefix=/opt/ffmpeg --enable-amr_nb --enable-amr_wb --enable-libogg --enable-libvorbis --enable-libgsm --enable-xvid --enable-liba52 --enable-libmp3lame --enable-gpl
Unknown option "--enable-amr_nb".
See ./configure --help for available options.

```

---

### Post by Cypher on 2008-01-28
As the error suggests, type "./configure --help" which will list all the available options. That particular website is asking you to use the latest copy of FFMPEG from the developers, but since the latest copy is in flux the options that were available at one point can be removed, renamed or re-arranged..so look at the help for more information.

---

