---
title: "Problems compiling source code"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by marytgras on 2006-08-27
So, I'm trying to install a program called q light control (for programing dmx512 based lighting systems), and I've already entered in apt-get build-essential to get the basic compiling packages.  I run the following command and here is the output:

 sudo ./configure ; make
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) gawk
configure: error: cannot run /bin/sh config/config.sub
make: *** No targets specified and no makefile found.  Stop. 

Okay, so can anybody tell me what I'm forgetting to execute, or packages or dependencies I've forgotten?  Thanks in advance,

-Marty

---

### Post by marytgras on 2006-08-27
Oh yeah, I forgot to mention, but as a side note I have already installed DMX4Linux from the ubuntu repositories.

---

### Post by croak77 on 2006-08-27
First, try running ./configure as a user not sudo.

Second, there is a Ubuntu package for 2.5-0 at there sourceforge page.

[http://sourceforge.net/project/showfiles.php?group_id=44856](http://sourceforge.net/project/showfiles.php?group_id=44856)

---

### Post by bodhi.zazen on 2006-08-27
I agree with croak77 - Use the repositories.

As far as your configure....

Looks like you need to install gawk, or the develop files.

---

### Post by marytgras on 2006-08-27
I checked the .deb package for q light, but that package is just the fixture libraries, not the actual program or source code.  I'll try installing gawk, and get back to you.

---

### Post by marytgras on 2006-08-27
Okay, I figured it out! I already had gawk, but what I needed was automake and autoconf, plus the libtools packages that are readily available in the repositories.  For anyone that wants to install this program (Q Light Controller) make sure you have what I mentioned, and follow the the directions in the readme file. ie,:

./bootstrap

./configure

make

sudo make install

the bins end up in usr/local/bin

double click or set up a launcher and you're good to go.

---

### Post by croak77 on 2006-08-28
> **marytgras said:**
> I checked the .deb package for q light, but that package is just the fixture libraries, not the actual program or source code.  I'll try installing gawk, and get back to you.

That's cause there is two .deb's, qlc-fixtures_2.5-0_ubuntu_i386.deb and qlc_2.5-0_ubuntu_i386.deb.

---

