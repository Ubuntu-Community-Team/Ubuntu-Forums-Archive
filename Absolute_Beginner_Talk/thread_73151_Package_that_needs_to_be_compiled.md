---
title: "Package that needs to be compiled"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by PatrickMay16 on 2005-10-08
Hello, 

I've come across something which needs to be compiled. It's the Last.fm AudioScrobbler plugin for XMMS.

It says you need to untar it into a directory, ./configure, make, make install, and it's installed.

However, when I do ./configure, I get this.
```

patrick@ubuntu:~/junk/xmms-scrobbler-0.3.6$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
patrick@ubuntu:~/junk/xmms-scrobbler-0.3.6$ 

```

So, I guess my problem is that I need a C compiler installed, but don't have one. What's the solution to this problem?

I'd greatly appreciate help.

---

### Post by ow50 on 2005-10-08
Install package "build-essential".

---

### Post by SGC on 2005-10-08
If you are using breezy, then just apt-get it (from the universe repository):
apt-get install xmms-scrobbler

---

### Post by PatrickMay16 on 2005-10-08
[QUOTE=ow50]Install package "build-essential".[/QUOTE]
Yes! This solved my problem.
Thanks very much!

---

