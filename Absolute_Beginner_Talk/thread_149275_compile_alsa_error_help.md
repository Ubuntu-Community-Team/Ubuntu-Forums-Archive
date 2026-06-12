---
title: "compile alsa error **help**"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by screamingindigital on 2006-03-23
hello all,  i am trying again to get some sound out of ubuntu.  i am trying to compile the alsa source and i get the following errors:

admin@ubuntu2:~/alsa-driver-1.0.11rc4$ ./configure --with-cards=cmipci --with-sequencer=yes;make;make install
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/admin/alsa-driver-1.0.11rc4
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
make all-deps
make[1]: Entering directory `/home/admin/alsa-driver-1.0.11rc4'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/admin/alsa-driver-1.0.11rc4'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/home/admin/alsa-driver-1.0.11rc4/acore'
Makefile:6: /home/admin/alsa-driver-1.0.11rc4/Makefile.conf: No such file or directory
/home/admin/alsa-driver-1.0.11rc4/Rules.make:75: /Rules.make1: No such file or directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/home/admin/alsa-driver-1.0.11rc4/acore'
make: *** [install-modules] Error 1


i tried doing this as sudo also and received the same results.  My sound card is a CMedia 8738 and breezy and dapper both see it but it will not work.  i am currently using dapper.  any help????

---

### Post by gord on 2006-03-23
you need your kernel's header files
```
sudo apt-get install linux-kernel-headers
```

---

### Post by screamingindigital on 2006-03-23
Thanks....I'm about 99% done w/ this.  The alsa-driver, library all compile, make and make install.  The only problem I am having is w/ the alsa-utilities.  It will compile but I get errors when I 'make' and 'make install'.  I'm not at my computer right now but I will post the errors when I get home.  I just do not understand why ubuntu will not produce sound in any of the 3 sound cards that I have tried (suse, fedora, dsl, and pclinuxos all can 'see' and install them w/o any problems or modprobes.  I really want to use breezy or dapper but fedora  is taking the lead w/ me right now. :(

---

