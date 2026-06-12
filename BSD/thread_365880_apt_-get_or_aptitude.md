---
title: "apt -get or aptitude????"
date: 2007-02-20
forum: BSD
---

### Post by shadowphoenix on 2007-02-20
I am wondering what is the command that is being used in the FreeBSD6.1.For example in Ubuntu we have aptitude and also apt-get what is the command for FreeBSD6.1.Thanks in advance.

---

### Post by Sbarton on 2007-02-20
Maybe not a answer to your specific question but try this link 
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/index.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/index.html)
regards

---

### Post by bapoumba on 2007-02-20
Moved to the "BSD" forum.

---

### Post by Yossarian on 2007-02-20
You can manage packages by running sysinstall.

However, only very important packages are in there.  For anything else you can go to the ports collection.  Check out the BSD handbook for more info.

I was sort of hoping this would be a thread about the creation of some kind of Frankensystem by manually installing APT on a FreeBSD system.  Anyone think this could work?  I imagine you could run Linux binaries from Debian's repos through the compatability layer, but could you possible install from source and get native BSD programs?

---

### Post by runningwithscissors on 2007-02-22
> **shadowphoenix said:**
> I am wondering what is the command that is being used in the FreeBSD6.1.For example in Ubuntu we have aptitude and also apt-get what is the command for FreeBSD6.1.Thanks in advance.

```
# cd /usr/ports
# make search name="<packagename>"
```
to search for a package, which will show you where it is in the tree.
Then,
```
# cd /usr/ports/<package-location>
# make config
```
to configure any options, if available.
```
# make install
```
to build and install
```
# make clean
```
to get rid of copy in the local directory
```
# make deinstall
```
to uninstall the package.

Short, sweet but probably not enough.
For more information,
[Linkage](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/ports.html)

---

