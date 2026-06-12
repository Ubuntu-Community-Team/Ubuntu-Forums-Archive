---
title: "iphone 5s problems syncing"
date: 2014-11-13
forum: Apple Hardware Users
---

### Post by makokitten2 on 2014-11-13
Hi everyone I've been trying to get my iphone 5s to sync with ubuntu and I've been trying to install all these different packages to get it operational and been running into a few problems. Currently I am trying to install libplist and it is giving me errors. It let me do ./configure, but when I tried to make the file it gave me this error.

makokitten@Darkstalker:~/makokitten/libplist-1.12$ make
make  all-recursive
make[1]: Entering directory `/home/makokitten/makokitten/libplist-1.12'
Making all in libcnary
make[2]: Entering directory `/home/makokitten/makokitten/libplist-1.12/libcnary'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/makokitten/makokitten/libplist-1.12/libcnary'
Making all in src
make[2]: Entering directory `/home/makokitten/makokitten/libplist-1.12/src'
  CXX      Node.lo
../libtool: line 1125: g++: command not found
make[2]: *** [Node.lo] Error 1
make[2]: Leaving directory `/home/makokitten/makokitten/libplist-1.12/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/makokitten/makokitten/libplist-1.12'
make: *** [all] Error 2

So now I'm trying to get it all running and I'm not quite sure what to do at this point. If someone has some advice to help me out I'd really appreciate it. It also asked me to install python development so I did that and it went pretty smoothly.

Thank you for any help anyone can provide,
makokitten

---

### Post by bashiergui on 2014-11-16
I gave up long ago trying to get iPhones to work with Ubuntu. It seemed to me Apple did everything possible to break functionality as soon as linux worked it out. I can't help you get the iPhone working.

I can help you resolve that particular error, though. It's looking for g++ which is part of the gcc compiler. Install gcc and all its dependents, then retry making libplist. Details on how to install gcc:[https://help.ubuntu.com/community/InstallingCompilers](https://help.ubuntu.com/community/InstallingCompilers)

---

### Post by makokitten2 on 2014-12-11
Thank you very much, I'll check that out and see if I can get it running.... wish me luck heh

---

