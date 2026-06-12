---
title: "package compiling"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by bellzii on 2007-03-18
hey everyone,

i was trying to compile a package , first i wrote,  ./bootstrap   and then i got error:

checking for swig... /usr/bin/swig
checking for SWIG version... 1.3.28
configure: error: SWIG version >= 1.3.31 required

I already downloaded that version and i built it ??
can some1 help

---

### Post by bellzii on 2007-03-18
hey everyone,

i was trying to compile a package , first i wrote in the terminal  ./bootstrap and then i got error:

checking for swig... /usr/bin/swig
checking for SWIG version... 1.3.28
configure: error: SWIG version >= 1.3.31 required

I already downloaded that version and i built it ?? but i still get that same error
can some1 help

---

### Post by bellzii on 2007-03-18
hey everyone,

i was trying to compile a package , first i wrote, ./bootstrap and then i got error:

checking for swig... /usr/bin/swig
checking for SWIG version... 1.3.28
configure: error: SWIG version >= 1.3.31 required

I already downloaded that version and i built it ??
can some1 help

---

### Post by annda on 2007-03-18
maybe try getting rid of the old .28 version? make sure latest compiled version is in /usr/bin/swig

other that that, are you tring to compile something that is not in the repositories?

plus, asking for compilation assistance on a beginner forum can take time to get answers, so do not post the same question every couple of minutes.

---

### Post by konst88 on 2007-03-18
The swig version on the repositories isn't the newest one.
You need to install or compile newer version of it.

---

### Post by bellzii on 2007-03-18
I downloaded the newest from debian but how can i install it

---

### Post by konst88 on 2007-03-18
If it is a deb file, just dbl click it.

---

### Post by bellzii on 2007-03-18
its a deb file but when i dbl click it i get a window as if its a compressed tar ,with 2 folders  : control.tar.gz and data.tar.gz
and a file called  debian-binary

---

### Post by konst88 on 2007-03-18
sudo dpkg -i filename.deb

---

### Post by annda on 2007-03-18
there is a precompiled package for feisty, but you will have to tace care of dependencies yourself:
[http://packages.ubuntu.com/feisty/interpreters/swig](http://packages.ubuntu.com/feisty/interpreters/swig)

---

### Post by bellzii on 2007-03-18
Thanks alot pal ;-)

---

### Post by Mr. C. on 2007-03-18
config found an older version.  You will need to tell the configure script where to find your newer version.

./configure --help | grep -i swig

MrC

---

### Post by bapoumba on 2007-03-18
@ bellzii: I've merged in here two other similar threads of yours with answers, and will be deleting the two other unanswered ones.
Please do not penta-plicate your threads in different forums, this will not help you getting more answers and is not recommended here. Bumping a thread a couple times a day is okay. Thanks.

---

