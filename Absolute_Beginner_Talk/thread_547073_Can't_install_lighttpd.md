---
title: "Can't install lighttpd"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by W13 on 2007-09-09
I downloaded lighttpd and managed to unzip it (so it's a folder now)

Then I opened the Terminal and followed the instructions... but the output reads:

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables

I went into FireFox and went to [http://localhost](http://localhost) but nothing. So... it's not installed properly. I wanna get Lighttpd, PHP, mySQL, FastCGI, and XCache installed on my fresh new Ubuntu that I installed like 25 mins ago.


Any help?

---

### Post by DBStevens on 2007-09-09
Where did you get your copy of lighttpd from, and running configure doesn't do the install it just checks the environment and builds the required make files to actually put the package together so it can be installed.

You might find synaptic to be much easier.

But if you want to go the configure/make/make install route I'll help provided I can get the same things you are using to do the install with.

---

