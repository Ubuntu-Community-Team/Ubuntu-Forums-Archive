---
title: "Having troubles with &quot;make&quot;"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by shelbeast on 2007-06-29
Hey People,

So I am a bit new to the world of Linux and Ubuntu specifically, Yet I am not all that new to the world of command line. I have used terminal quite a bunch in Mac OS X, my primary operating system, but something here I am trying to install using the same commands as the logs are telling me and also as I remember doing before. But it is telling me that I have to specify a makefile. Now I have tried doing a make -f makefile.am, and a makefile.in, for those are the only make files that I see in the compiz directory. If there is someone who could help with that would be awesome.

I am running Ubuntu 7.04 on a Macbook using VMware.

---

### Post by chamberlain2006 on 2007-06-29
Those .in and .am files are used to configure the Makefile.  You usually have to run ./configure first to configure it, and then make/sudo make install.

---

### Post by cwood06 on 2007-06-29
If you are trying to update compiz try getting the repo from the compiz-fusion tutorial. It will download the newest version.

---

