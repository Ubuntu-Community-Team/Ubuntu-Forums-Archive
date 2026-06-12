---
title: "apt-get, distro, or off the net"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2007-02-23
sometimes i dont see something in the depositories, but then following instructions i type "sudo apt-get xxxxxx-xxxx-xx" and then it finds it and runs it! YAY!  i love the depositories for ease of use but i also find apt-get neater than the depositories simply because it "just knows" where it is.  how does it know?  where does it look?  can i apt-get something i want in that isnt in the depositories if i know the file location ie. ftp:domain.com/public/linuxprogram.tar.bz2

if i just find and download a tarball, is it better to compile it myself or to download the official linux binary.  also is there a step by step guide for turning a tarball into a program (both from source and binary) into it's typical directory and a nice icon under applications?

---

### Post by Bachstelze on 2007-02-23
In a nutshell, when you run apt-get update, it downloads a list of all installable packages and the location of the DEB files. So when you apt-get install something, it just downloads the DEB from the location mentioned in the index and installs it.

Whether it is better to compile from source or use the Ubuntu packages is a matter of choice. Tou can find a comparison of source Vs packages [here](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/ports-overview.html). It for FreeBSD but mostly applies to Linux too.

---

### Post by houstonbofh on 2007-02-23
Start here.
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

Also read here.
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Both sites have a lot of other good information for beginners.  (And some experts)

---

### Post by nonewmsgs on 2007-02-23
thank you.  that was most helpful and extremely informative.:popcorn:

---

