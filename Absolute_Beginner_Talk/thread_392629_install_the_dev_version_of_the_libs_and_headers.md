---
title: "install the dev version of the libs and headers"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by pennst26 on 2007-03-24
I am new to ubuntu and linux and not quite sure what he means when he gave me this advice.
I was installing GLFTPD
and I got these errors
```
5. COMPILING SOURCES & COPYING LIBS:
------------------------------------

modifying source (bin/sources/glconf.h) ... OK.
Compiling source files in /glftpd/bin/sources to /glftpd/bin:
   ansi2gl .. FAILED!
   dirlogclean .. FAILED!
   dirloglist .. FAILED!
   dirlogscanner .. FAILED!
   dirlogsearch .. FAILED!
   dupeadd .. FAILED!
   dupecheck .. FAILED!
   dupediradd .. FAILED!
   dupelist .. FAILED!
   dupescan .. FAILED!
   flysfv .. FAILED!
   ftpwho .. FAILED!
   glupdate .. FAILED!
   killghost .. FAILED!
   nukelogclean .. FAILED!
   nukelogscanner .. FAILED!
   olddirclean2 .. FAILED!
   undupe .. FAILED!
   userstat .. FAILED!
   weektop .. FAILED!
   Failed to compile: /glftpd/bin/sources/ansi2gl.c
   Failed to compile: /glftpd/bin/sources/dirlogclean.c
   Failed to compile: /glftpd/bin/sources/dirloglist.c
   Failed to compile: /glftpd/bin/sources/dirlogscanner.c
   Failed to compile: /glftpd/bin/sources/dirlogsearch.c
   Failed to compile: /glftpd/bin/sources/dupeadd.c
   Failed to compile: /glftpd/bin/sources/dupecheck.c
   Failed to compile: /glftpd/bin/sources/dupediradd.c
   Failed to compile: /glftpd/bin/sources/dupelist.c
   Failed to compile: /glftpd/bin/sources/dupescan.c
   Failed to compile: /glftpd/bin/sources/flysfv.c
   Failed to compile: /glftpd/bin/sources/ftpwho.c
   Failed to compile: /glftpd/bin/sources/glupdate.c
   Failed to compile: /glftpd/bin/sources/killghost.c
   Failed to compile: /glftpd/bin/sources/nukelogclean.c
   Failed to compile: /glftpd/bin/sources/nukelogscanner.c
   Failed to compile: /glftpd/bin/sources/olddirclean2.c
   Failed to compile: /glftpd/bin/sources/undupe.c
   Failed to compile: /glftpd/bin/sources/userstat.c
   Failed to compile: /glftpd/bin/sources/weektop.c

```
I asked for help in their support channel and this was the reply that I don't understand.
```
1:09a    (``26``) 11:20a    (``26``) any idea what would cause that to not compile?
  1:09a    (``26``)   11:21a    (``26``) just says filed, no other error message
  1:09a    (``26``)   11:21a    (``26``) failed*
  1:09a    (``26``)   11:22a    (@psxc) install the dev version of the libs and headers
  1:09a    (``26``)   11:23a    (@psxc) gcc is probably unable to compile anything.
```

Can someone walk me thru what exactly that means?

---

### Post by lloyd_b on 2007-03-24
First thing to try - in a terminal window:
```
sudo apt-get install build-essential
```

This will ensure that you have all of the packages you need for a working compiler.  Then try compiling again and see what happens.

You may need some additional packages.  What "(@psxc)" was talking about is that for a given library package (such as "libgtk1.2"), there is usually a "development" package (in this case, "libgtk1.2-dev") which contains the various "header" files required to compile against that package.  So you may need to install some "...-dev" packages for the libraries used by that program.

Sorry, I can't tell you which packages are required, as I'm not familiar with GLFTPD.  Hopefully they have a website or something that lists the requirements.

Lloyd B.

---

### Post by pennst26 on 2007-03-24
thank you, thank you, thank you =D

wish I would have asked sooner, I have tried different things for some time.

```
modifying source (bin/sources/glconf.h) ... OK.
Compiling source files in /glftpd/bin/sources to /glftpd/bin:
   ansi2gl .. OK.
   dirlogclean .. OK.
   dirloglist .. OK.
   dirlogscanner .. OK.
   dirlogsearch .. OK.
   dupeadd .. OK.
   dupecheck .. OK.
   dupediradd .. OK.
   dupelist .. OK.
   dupescan .. OK.
   flysfv .. OK.
   ftpwho .. OK.
   glupdate .. OK.
   killghost .. OK.
   nukelogclean .. OK.
   nukelogscanner .. OK.
   olddirclean2 .. OK.
   undupe .. OK.
   userstat .. OK.
   weektop .. OK.
All source files successfully compiled.
```
Much appreciation lloyd =D

---

