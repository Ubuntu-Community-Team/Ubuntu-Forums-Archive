---
title: "how to install SICStus Prolog"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by cluelessCS on 2007-06-24
Hi

Trying to install SISCtus Prolog under ubuntu 7.04. 
I am new to Linux, and therefore almost completely ignorant of anything related to a Linux command line interface. (even though I am fairly competent with computers, being a CS major who managed to avoid Linux so far).

here's the list of problems:

(1) which version to download? 
[http://www.sics.se/isl/sicstuswww/site/download4.html](http://www.sics.se/isl/sicstuswww/site/download4.html)
They make a distinction between glibc2.3 and glibc2.2. Which one corresponds to ubuntu 7.04?

(2) Prerequisites?
Java, Tcl/Tk and Berkeley DB are listed as prerequisites here.
[http://www.sics.se/isl/sicstuswww/site/portability.html](http://www.sics.se/isl/sicstuswww/site/portability.html)
Are those installed on a fresh ubuntu installation? (not that I would even know what Tcl/Tk and Berkeley DB are actually doing...)

(3) the actual installation: how to?
the release note of SICStus prolog says to call an installation script with
% ./InstallSICStus
That doesnt work. response: no such job. what is '%' supposed to do?
I then tried 'sh ./InstallSICStus', which, IIRC, means executing a shell script.

That leads me to the next problem.

(4) error during installation
The installation script seems to run okay when called with 'sh', but responds with some errors soon:
> 
Checking installation cache... install.cache
dummy.c:1:19: error: stdio.h: No such file or directory
dummy.c:2:30: error: gnu/libc-version.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:1:19: error: stdio.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:2:22: error: features.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c: In function ‘main’:
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:13: warning: incompatible implicit declaration of built-in function ‘printf’
Glibc header files and runtime system disagree on version.
Header files:   x86-linux

Maybe at this point you will point out that this is a question rather for the SICStus forum/support...

I cant really judge if my error is related to something described in this FAQ:
[http://intranet.cs.man.ac.uk/software/sicstus/faq.html](http://intranet.cs.man.ac.uk/software/sicstus/faq.html)
saying:
> This error message appears when SICStus has been compiled using a different version of libc.so than your machine has installed. The message "no such file or directory" does not refer to sp.exe but to the particular libc.so version that SICStus expects.
> SICStus is currently available as binary distributions for libc.so.6, a.k.a. glibc, versions 2.0 and 2.1. Make sure to download the correct version.

How do I know which version of libc is installed with ubuntu? (perhaps this questions is related to my question (1))


Thanks

 - Michael

---

