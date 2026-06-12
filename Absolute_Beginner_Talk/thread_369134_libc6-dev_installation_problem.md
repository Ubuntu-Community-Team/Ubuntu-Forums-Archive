---
title: "libc6-dev installation problem"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by johnnyxf on 2007-02-24
greetings.

the short version.
i need the latest version of ndiswrapper for [yet another] attempt to get a wireless connection working

TacoSupreme at ndiswrapper forums tells me i need libc6-dev libraries installed to do this. 
i got this package from
[http://packages.debian.org/testing/libdevel/libc6-dev]("http://packages.debian.org/testing/libdevel/libc6-dev")
but if refuses to install - unsatisfied dependency errors:

- libc6-dev depends on libc6 (= 2.3.6.ds1-11); however: version of libc6 on system is 2.4-1ubuntu12.
- libc6-dev depends on linux-kernel-headers; however: Package linux-kernel-headers is not installed

can anyone help me out, please?
is there a version of libc6-dev for ubuntu?

---

### Post by Maestro23 on 2007-02-24
If you have enabled extra repositories, this should work:

> sudo aptitude update

sudo aptitude install libc6-dev

---

### Post by johnnyxf on 2007-02-24
thanks maestro23.

i have already tried that, but i believe that an internet connection is required?

sudo aptitude update returns lines such as
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Temporary failure resolving 'security.ubuntu.com'

which i take as meaning that it is looking up a URL and failing to find it.

is there a way of getting these files as a tarball? i can dl files to the other machine and transfer them by cd.

---

