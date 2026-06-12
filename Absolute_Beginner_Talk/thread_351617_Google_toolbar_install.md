---
title: "Google toolbar install"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2007-02-02
I am trying to install this new toolbar from google.
[http://code.google.com/p/avant-window-navigator/](http://code.google.com/p/avant-window-navigator/)

I have cd to directory ran ./configure and get the followign error.

caippers@caippers-desktop:~/avant$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
caippers@caippers-desktop:~/avant$ 


Any suggestions.  Also where is config.log not that it would really help me.

---

### Post by xgrendel on 2007-02-02
Generally speaking, that is a compiler issue. You will want to update the GCC compiler and possibly use the glibc-devel package. Try the following (I'm not at a Linux box to verify this)

sudo apt-get install build-essential

---

### Post by gentlemanmasher on 2007-02-02
I'll give it a try when I get home thanks.

---

### Post by h2gofast on 2007-02-02
nice Clockwork Orange avatar.

---

### Post by gentlemanmasher on 2007-02-02
Thanks I'm a bit fond of it myself.  Great movie.

By the way if anyone is looking at how to install this toolbar please see the following thread.  I happened to see this on Digg today.

[http://ubuntuforums.org/showthread.php?p=2093300](http://ubuntuforums.org/showthread.php?p=2093300)

I haven't tried it yet but it will solve my problem.

---

