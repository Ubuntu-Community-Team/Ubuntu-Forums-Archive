---
title: "Can someone help me get the  acceptable &quot;C&quot; compiler..??"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-09-24
> sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  g++ g++-4.0 gcc gcc-4.0 libc6 libc6-dev libc6-i686 libstdc++6-4.0-dev
  linux-kernel-headers
Suggested packages:
  gcc-4.0-doc lib64stdc++6 manpages-dev autoconf automake1.9 libtool flex
  bison gcc-doc gcc-4.0-locales libc6-dev-amd64 lib64gcc1 glibc-doc
  libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  build-essential g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 8 newly installed, 0 to remove and 196 not upgraded.
Need to get 14.1MB of archives.
After unpacking 34.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main libc6 2.3.5-1ubuntu12.5.10.1 [4872kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main libc6-i686 2.3.5-1ubuntu12.5.10.1 [1008kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main linux-kernel-headers 2.6.11.2-0ubuntu13 [1037kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main libc6-dev 2.3.5-1ubuntu12.5.10.1 [2792kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main gcc-4.0 4.0.1-4ubuntu9 [498kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main gcc 4:4.0.1-3 [4910B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libstdc++6-4.0-dev 4.0.1-4ubuntu9 [1517kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libstdc++6-4.0-dev 4.0.1-4ubuntu9
  Connection timed out [IP: 195.248.90.23 80]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main g++-4.0 4.0.1-4ubuntu9 [2323kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main g++ 4:4.0.1-3 [1382B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main build-essential 11.1 [6826B]
Fetched 12.5MB in 1h15m43s (2761B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb)  Connection timed out [IP: 195.248.90.23 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
jason@Hp-Vectra-VL:~/hplip-1.6.7$ sudo --fix-missing
sudo: please use single character options
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
jason@Hp-Vectra-VL:~/hplip-1.6.7$ --fix-missing
bash: --fix-missing: command not found
jason@Hp-Vectra-VL:~/hplip-1.6.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
jason@Hp-Vectra-VL:~/hplip-1.6.7$


I'm trying to install something and it's not installing..

---

### Post by MWAAAHAAA on 2006-09-24
> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...untu9_i386.deb](http://us.archive.ubuntu.com/ubuntu/...untu9_i386.deb) Connection timed out [IP: 195.248.90.23 80]

Seemed that either your computer or the server had problems when fetching this package. I just tried to download it ([http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb)) and it worked out fine for me. I suggest you just try another apt-get upgrade. If it still fail to get the package after that, try selecting a different package mirror. If it still doesn't work after that, come back and post.

---

### Post by jason.b.c on 2006-09-24
> **MWAAAHAAA said:**
> Seemed that either your computer or the server had problems when fetching this package. I just tried to download it ([http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb)) and it worked out fine for me. I suggest you just try another apt-get upgrade. If it still fail to get the package after that, try selecting a different package mirror. If it still doesn't work after that, come back and post.

So thats all i'm missing then..?

Can i just download it and install it manually..?

---

### Post by MWAAAHAAA on 2006-09-24
Your problem is that the packages got downloaded, but *not* installed as apt-get was unable to fetch the libstdc++-dev package. This means that although you can install this package manually, you still need the other packages installed. I would suggest the following course of action:

apt-get update
apt-get upgrade

If at this point you still get the same error, try ignoring the missing package:

apt-get update --ignore-missing

To install a downloaded package manually, you can use

wget [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb)
dpkg -i /location/to/where/you/saved/libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb

Of course, don't forget to run those commands with sudo. Otherwise you can't install anything.

I noticed something else in your log:

> E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
 jason@Hp-Vectra-VL:~/hplip-1.6.7$ sudo --fix-missing


It meant you had to run apt-get update --fix-missing, not just --fix-missing. When a string is prepended by - or -- it is an option that is to supplied to a command.

---

### Post by jason.b.c on 2006-09-24
Does this mean it installed now.? , I think it did..:D 

> sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  g++ g++-4.0 gcc gcc-4.0 libc6 libc6-dev libc6-i686 libstdc++6-4.0-dev
  linux-kernel-headers
Suggested packages:
  gcc-4.0-doc lib64stdc++6 manpages-dev autoconf automake1.9 libtool flex
  bison gcc-doc gcc-4.0-locales libc6-dev-amd64 lib64gcc1 glibc-doc
  libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  build-essential g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 8 newly installed, 0 to remove and 196 not upgraded.
Need to get 1517kB/14.1MB of archives.
After unpacking 34.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libstdc++6-4.0-dev 4.0.1-4ubuntu9 [1517kB]
Fetched 1423kB in 12m56s (1833B/s)

Preconfiguring packages ...
(Reading database ... 62761 files and directories currently installed.)
Preparing to replace libc6 2.3.5-1ubuntu12 (using .../libc6_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.3.5-1ubuntu12.5.10.1) ...
Current default timezone: 'America/Chicago'.
Local time is now:      Sun Sep 24 07:33:47 CDT 2006.
Universal Time is now:  Sun Sep 24 12:33:47 UTC 2006.
Run 'tzconfig' if you wish to change it.

(Reading database ... 62734 files and directories currently installed.)
Preparing to replace libc6-i686 2.3.5-1ubuntu12 (using .../libc6-i686_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Unpacking replacement libc6-i686 ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up libc6-i686 (2.3.5-1ubuntu12.5.10.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
Setting up libc6-dev (2.3.5-1ubuntu12.5.10.1) ...
Setting up gcc-4.0 (4.0.1-4ubuntu9) ...
Setting up gcc (4.0.1-3) ...

Setting up libstdc++6-4.0-dev (4.0.1-4ubuntu9) ...
Setting up g++-4.0 (4.0.1-4ubuntu9) ...
Setting up g++ (4.0.1-3) ...

Setting up build-essential (11.1) ...
jason@Hp-Vectra-VL:~/hplip-1.6.7$


---

### Post by MWAAAHAAA on 2006-09-24
Yep, looks allright to me. Seems the there were some problems when you were downloading the first time.

---

### Post by jason.b.c on 2006-09-24
Ah crud.! , Now what's missing..???

I'm trying to install  [[SIZE="4"]This..[/SIZE]]("http://hplip.sourceforge.net/screenshots.html")

> cd /home/jason/hplip-1.6.7
jason@Hp-Vectra-VL:~/hplip-1.6.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for a Python interpreter with version >= 2.2... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for chkconfig... no
checking for install_initd... no
checking for pthread_create in -lpthread... yes
[B]checking for CRYPTO_free in -lcrypto... no
checking for snmp_timeout in -lnetsnmp... no
checking for usb_init in -lusb... no[/B]
**configure: error: cannot find libusb support**
jason@Hp-Vectra-VL:~/hplip-1.6.7$ make
make: *** **No targets specified and no makefile found.**  Stop.
jason@Hp-Vectra-VL:~/hplip-1.6.7$


---

### Post by jason.b.c on 2006-09-24
Thought i would mention the other thread i [started on this before..]("http://www.ubuntuforums.org/showthread.php?t=246968")

Just in case..

---

### Post by distroman on 2006-09-24
I don't use that application, so I am sure. 
Seems to me like "configure: error: cannot find libusb" are missing. 
Maybe you are missing libusb-dev? 

[http://hplip.sourceforge.net/install/step2/debian.html](http://hplip.sourceforge.net/install/step2/debian.html)

---

### Post by jason.b.c on 2006-09-24
> **distroman said:**
> I don't use that application, so I am sure. 
Seems to me like "configure: error: cannot find libusb" are missing. 
Maybe you are missing libusb-dev? 

[http://hplip.sourceforge.net/install/step2/debian.html](http://hplip.sourceforge.net/install/step2/debian.html)

```
sudo apt-get install python-dev libsnmp5-dev libcupsys2-dev python-qt3 lsb libusb-dev libjpeg62-dev
```

Downloading now , I'll post back in a bit..

---

### Post by jason.b.c on 2006-09-24
Well i thought i would post back here now ( been a while huh.? ) ..

It's installed now :D , I finally got the HP Toolbox..Although it took alot to get it to install correctly..

Thank you everyone for your help....:D

---

