---
title: "Can i do cross compiling to PowerPc architecture?"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-07-13
Hi friends,

 If there is an installation package which is suited for the X86 architecture would it be possible to use some sort of a cross compiler to make it run in a Powerpc environment?

  I know that the rpm packages are made available by using "alien " command but along the same lines is there any other cross compiler?

Any suggestions or possible pointers are most welcome.

Thanks a lot

---

### Post by %hMa@?b&lt;C on 2006-07-13
what is the package?  You could try compiling it from source (if available)

---

### Post by hotbrainz on 2006-07-13
the package is for an embedded web server - "Mbed this" Appweb. the source package can be obtained but how can I possibly cross compile it?
What do i need to do this ?

Please elaborate, I am not an expert in any of this.

Thanks a lot for the help

---

### Post by %hMa@?b&lt;C on 2006-07-13
ok, I think I can help you here
first, try the rpm source [http://www.appwebserver.org/software/appWeb-src-2.0.5-4.rpm.gz](http://www.appwebserver.org/software/appWeb-src-2.0.5-4.rpm.gz)
then if that doesnt work, do the following
```
 wget http://www.appwebserver.org/software/appWeb-src-2.0.5-4.tar.gz
```
```
tar xzf appWeb-src-2.0.5-4.tar.gz
```
```
cd appWeb-2.0.5
```
```
./configure
```
```
make
```
```
make install
```
that should do it!

---

### Post by hotbrainz on 2006-07-13
Thanks dude, but that will install the package in Ubuntu which is great. but i need it for PowerPC architecture. Is there a cross compiler for that sort of thing!

Or am i just being stupid here by missing something?

Cheers

---

### Post by %hMa@?b&lt;C on 2006-07-13
that will install using your powerpc arch.  thats what ./configure does, makes it usse your archetecture

---

