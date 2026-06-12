---
title: "package installers broken, strange errors"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2006-09-01
Ok, when I run synaptec I get:
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
when I follow the instructions and run dpkg --configure -a I get
```
richard@AKIRA:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted
```
I've tried re-downloading all the packages and everything else I can think of. Any Help'd be much appreciated!

---

### Post by Kobalt on 2006-09-01
Hello,

Have you tried running Synaptic and selecting "repair brocken packages" from the Edition menu ? 

Cheerios !

---

### Post by richardward101 on 2006-09-01
Yes, nothing happens.

---

### Post by richardward101 on 2006-09-02
Anyone got any ideas? Its really beginning to be annoying.

---

### Post by richardward101 on 2006-09-02
found a fix here [http://techxplorer.wordpress.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/]("http://techxplorer.wordpress.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/")

---

