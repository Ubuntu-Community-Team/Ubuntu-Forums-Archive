---
title: "Last.FM with XMMS help"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by EBAR on 2006-03-30
I was at [www.last.fm](www.last.fm) today and wanted to try it out. I followed their instructions and downloaded a tar for XMMS. I followed the instructions in the readme and install file and untarred the file. The instructions tell me to  ./configure   and then to      make     and the to     make install. I've never compiled from source so I may being making an obvious mistake but I can't even get past   ./configure    here is what I get....

```
matt@ubuntu:~/xmms-scrobbler-0.3.6$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```


Any help in this matter is greatly appreciated. I will be off the computer for a couple hours but I'll be back as soon as possible. Thank you in advance.

EBAR

---

### Post by Sef on 2006-03-30
in order to comple,yYou need to download build-essential.

sudo apt-get update

sudo apt-get install build-essential


Also you can download xmms, via Add Applications (Applications > Add Applications > Sound & Video > more programs), or synaptic, or command line (sudo apt-get update then sudo apt-get install xmms.)

---

### Post by EBAR on 2006-03-30
Thank you very much Sef. I already had XMMS, but I installed what you said and it worked without a problem!!

Thanks again!


EBAR

---

### Post by Sef on 2006-03-30
You're welcome.  Glad I could help you.

---

### Post by Jenda on 2006-04-02
In fact, "sudo apt-get install xmms-scrobbler" works just as well

---

