---
title: "getting sources?  and stdc++ not found"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by bodhidharma on 2006-05-03
Hi friends,

Pretty basic question:  I was going to fool around with some automated downloading
of data from various web sites, and I thought I might hack a little myself, but it
always helps to see other people's solutions to the same problems, so I thought
I would look at the source of ht://Dig (hooray open source!)... but how do I get
the source?  It should sort of come along for free, but where is it?

OK, so I thought if I don't know how to do that, I could just go to sourceforge and
get the source tarball, which I did quite easily.  Then I unpacked it and ran
"./configure" ... a surprising number of failures (e.g.:
 checking for socket in -lsocket... no
 checking for t_accept in -lnsl... no
 checking for deflate in -lz... no
and many more)
then a fatal error: 
 checking for ostream.h... no
 checking for iostream.h... no
 checking for fstream.h... no
 configure: error: To compile ht://Dig, you will need a C++ library. Try installing
   libstdc++.

But I *do* have libstdc++.  Why can't it find it?  Is there some missing
environment variable -- if so, why?

Thanks!

---

### Post by gborzi on 2006-05-03
To download the source package type
```
sudo apt-get source <packagename>
```
For the other problem, perhaps you have not installed the development package for libstdc++6, i.e. libstdc++6-4.0-dev. Almost every library in GNU/Linux distribution is splitted in the shared library package, that basically contains the .so.n files and the development package, that contains include files, .a library files and .so files.
The former is used by already compiled programs, i.e. binaries, the latter to compile source code.
I'm not sure, but it seems that the other failures are also due to the lack of the development packages for the libraries needed to compile the program.

---

### Post by linear on 2006-05-03
Before you can compile anything, you need the **build-essential** package:
```
sudo apt-get install build-essential
``` This item is worthwhile reading: [CompilingSoftware]("https://wiki.ubuntu.com/CompilingSoftware").

---

