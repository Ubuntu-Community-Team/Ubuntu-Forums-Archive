---
title: "Installation Issue with Kmymoney2 version 0.8.8.1"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by aabento on 2007-12-29
Hello

I downloaded the new version of kmymoney2 ( kmymoney2_o.8.8.1_i386.deb ) 
and when I try to install in Ubuntu 7.10 (Gutsy) I got following error:

Error : **Dependency is not satisfiable: Kdelibs4** ](*,)](*,)](*,)

I already installed Kdelibs4 through the *Synaptic Package Manager* but 
still with the same error. :(

How can I solve this error? :confused:

Arnaldo

---

### Post by dwblas on 2007-12-29
The error message you posted is incomplete and so of no value.  The first thing to check is if the installed version of kdelibs4 is the same as that in the error message.  Also you might try the --build-deps option of apt-get (man apt-get for more info).  If you are using dpkg, you can tell it to ignore the packages that this one depends on, which may or may not work with a different version installed (man dpkg this time).

---

### Post by oygle on 2008-01-01
This thread may help:

[http://comments.gmane.org/gmane.comp.kde.kmymoney2.user/1417](http://comments.gmane.org/gmane.comp.kde.kmymoney2.user/1417)

HTH

---

