---
title: "64-bit GCC issues (maybe?)"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by BradNeuman on 2007-02-01
Hey everyone this is my first post and I am not completely incompetent but I am kind of a Linux newb. I'm not totally sure if this should be on this section of the forum, but here it goes.

I am running version 6.06 on an AMD Turion 64 bit laptop. The instillation and everything went well in the beginning, until I tried to compile some code. At first I was trying to compile some program I downloaded and it gave me the following error:

checking for C compiler default output file name... configure: error: C compiler cannot create executables
.

Here's some stuff I think may be relevant from config.log, I can post more if necessary:

uname -m = x86_64
uname -r = 2.6.15-27-amd64-generic
uname -s = Linux
uname -v = #1 SMP PREEMPT Fri Dec 8 17:50:54 UTC 2006


/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = x86_64
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

configure:2316: gcc --version </dev/null >&5
gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2324: $? = 0
configure:2326: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2329: $? = 1
configure:2352: checking for C compiler default output file name
configure:2355: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status


When I tried to create a really simple "hello world" app I got the "/usr/bin/ld: crt1.o: No such file: No such file or directory" error. From my research this seems to have something to do with the 32 bit libraries, but I don't see why hello world couldn't compile in 64 bit mode.

thanks in advance,
Brad

---

### Post by taurus on 2007-02-01
Try

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by BradNeuman on 2007-02-01
Beautiful, I knew it was something simple. thanks :)

---

