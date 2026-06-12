---
title: "Compiling Xvidcap"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-05-20
Hello, I am trying to compile, [xvidcap from sourceforge](http://xvidcap.sourceforge.net/), and so at first I downloaded the debian, it had dependency errors, so I downloaded the tar.gz

Well, after I extract it, I don't have a configure script, and yet in the readme it states:
> COMPILATION:

Now, the usual triple does what most users want, so it's just:

./configure
make
make install

I don't know what to do. I searched the repositories first, it found it, but it said it really wasn't there, and I couldn't install it. Any ideas? or any other video capture program that is better and easier to install (preferably the repository)?

Sincerely,
Dr Small

---

### Post by MarilenCorciovei on 2007-05-21
Maybe you did not downloaded the right thing. I downloaded xvidcap-1.1.5.tar.gz found the configure, installed some additional devs: apt-get install libglade2-dev libXmu-dev and configure worked.

[Len]("http://www.len.ro")

---

### Post by charly4711 on 2007-05-24
I would second that statement. If I download the source from here:
[http://downloads.sourceforge.net/xvidcap/xvidcap-1.1.5.tar.gz?use_mirror=puzzle](http://downloads.sourceforge.net/xvidcap/xvidcap-1.1.5.tar.gz?use_mirror=puzzle)

There IS a configure file there.
Could you post where you obtained the source?
Also, the deb was build for feisty, so dependency problems on dapper have to be expected.

---

