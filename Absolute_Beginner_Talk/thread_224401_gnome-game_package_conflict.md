---
title: "gnome-game package conflict"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by revcol on 2006-07-27
I'm trying to update gnome games to resolve the crash in aisleriot.When I download the (.tar.gz) 1.2.14.2-1 (stable) package and convert it to a .deb package the Gdeb installer first warns me that a "later version exists, update thru software channels" and then when I close the warning window and click "Install Package" the installation fails with the message "librsvg2-common conflicts with gnome-games(<<1.12.14.2)
dpkg:error processing, conflicting packages, installation failed. How do I resolve this?

---

### Post by trent dillman on 2006-07-28
...

---

### Post by revcol on 2006-07-28
Trent: Thanks for the info, I'm using Ubuntu 6.0.6(Dapper) untar= command not found. Ray

---

### Post by revcol on 2006-07-28
Believe it or not, I have tried for 2 days to install  this update. See earlier posts.

/home/ray/Desktop/gnome-games-2.14.2.1.tar.gz . 
Extracted files to Desktop
cd to /home/ray/Desktop/gnome-games-2.14.2.1
type ./gnome-games-2.14.2.1
then I get this:
ray@UbuntuLearner:~/Desktop/gnome-games-2.14.2.1$ ./configure gnome-games-2.14.2.1
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gnome-games-2.14.2.1-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for gnome-games-2.14.2.1-g++... no
checking for gnome-games-2.14.2.1-c++... no
checking for gnome-games-2.14.2.1-gpp... no
checking for gnome-games-2.14.2.1-aCC... no
checking for gnome-games-2.14.2.1-CC... no
checking for gnome-games-2.14.2.1-cxx... no
checking for gnome-games-2.14.2.1-cc++... no
checking for gnome-games-2.14.2.1-cl... no
checking for gnome-games-2.14.2.1-FCC... no
checking for gnome-games-2.14.2.1-KCC... no
checking for gnome-games-2.14.2.1-RCC... no
checking for gnome-games-2.14.2.1-xlC_r... no
checking for gnome-games-2.14.2.1-xlC... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for intltool >= 0.29... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
ray@UbuntuLearner:~/Desktop/gnome-games-2.14.2.1$ (MAKE)
bash: MAKE: command not found
ray@UbuntuLearner:~/Desktop/gnome-games-2.14.2.1$ (make)
make: *** No targets specified and no makefile found.  Stop.
ray@UbuntuLearner:~/Desktop/gnome-games-2.14.2.1$ make
make: *** No targets specified and no makefile found.  Stop.
ray@UbuntuLearner:~/Desktop/gnome-games-2.14.2.1$ --build
bash: --build: command not found
ray@UbuntuLearner:~/Desktop/gnome-games-2.14.2.1$ make gnome-games-2.14.2.1
make: *** No rule to make target `gnome-games-2.14.2.1'.  Stop.
ray@UbuntuLearner:~/Desktop/gnome-games-2.14.2.1$

To say I'm a frustrated newbie is an understatement. Maybe I should post this under "Things I don't like about Ubuntu".

---

### Post by revcol on 2006-08-01
Thread Closed - Resolved With Package Update

---

