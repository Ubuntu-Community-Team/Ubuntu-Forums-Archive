---
title: "How can I install a specific version of an application"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by thewump on 2006-12-29
I'm having horrible performance issues with Evolution mail calling exchange server, and found some posts that indicate I might have more luck with 2.6.3.

Is there an easy way to specify a version when using apt-get, or another easy way to grab a specific version of a package?

I've tried downloading source, but haven't done this before, and when I follow the instructions after downloading source I get the error:

checking for C compiler default output file name... configure: error: C compiler cannot create executables

when I run ./configure

TIA

Keith

---

### Post by benuski on 2006-12-29
Are you sure you have build-essential and autoconf and gcc installed?  What I would do is to do a "sudo apt-get build-dep evolution", which will grab all of the dependencies for it.  Then unistall the version you have, and then again try to do a "./configure", "make", "sudo make install".

---

### Post by Sef on 2006-12-29
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

