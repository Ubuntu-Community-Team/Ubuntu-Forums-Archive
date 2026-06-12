---
title: "alsa-driver-1.0.10"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-11-27
Hey all!

Hope everyone is well. I just installed ubuntu a couple of days ago, i have absolutely no linux experience. I went to install the latest alsa-driver cause my sound doesn't work on my laptop :(. so when i ./configure in cd alsa-driver-1.0.10 it comes up w/ an error

adduds@ubuntu:~/alsa-driver-1.0.10$ ./configure
checking for gcc... gcc
checking for C compiler default output... a.out
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
checking for current directory... /home/adduds/alsa-driver-1.0.10
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
/*
The file /usr/src/linux/include/linux/version.h does not exist. 
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
*/
what does that mean?

---

### Post by bluetoad on 2005-11-27
First, it will be worth making sure that sound is definitely not working because you need to do this everytime you upgrade the kernel.  

You need to install the linux-headers package for the kernel version you are running.

1. First work out your version of the kernel (I'm sitting on a hoary box)

peter@alver:/tmp$ uname -a
Linux alver 2.6.10-5-686 #1 Mon Oct 10 11:28:02 UTC 2005 i686 GNU/Linux
               ^^^^^^^^

and then install linux-headers-2.6.10-5-686 in this case.  You can see the packages available in synaptic or doing 


peter@alver:/tmp$ apt-cache search linux-headers |grep 2.6.10-5
linux-headers-2.6.10-5 - Header files related to Linux kernel version 2.6.10
linux-headers-2.6.10-5-386 - Linux kernel headers 2.6.10 on 386
linux-headers-2.6.10-5-686 - Linux kernel headers 2.6.10 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.10-5-686-smp - Linux kernel headers 2.6.10 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.10-5-k7 - Linux kernel headers 2.6.10 on AMD K7
linux-headers-2.6.10-5-k7-smp - Linux kernel headers 2.6.10 on AMD K7 SMP


You could install the package in this example by

sudo apt-get install linux-headers-2.6.10-5-686

More complete alsa instructions (for HDA Intel drive on Hoary) at [https://wiki.ubuntu.com//HdaIntelSoundHowto](https://wiki.ubuntu.com//HdaIntelSoundHowto)

---

### Post by adduds on 2005-11-27
aight thanks man, that got me through the ./configure part but now during the make part i get 

make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/adduds/alsa-driver-1.0.10  modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/adduds/alsa-driver-1.0.10/acore/hwdep.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/adduds/alsa-driver-1.0.10/acore/hwdep.o] Error 127
make[2]: *** [/home/adduds/alsa-driver-1.0.10/acore] Error 2
make[1]: *** [_module_/home/adduds/alsa-driver-1.0.10] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [compile] Error 2

....hmmm, all looks like greek

---

### Post by bluetoad on 2005-11-27
You are missing the compiler so you'll need to install the gcc-3.4 package.  

sudo apt-get install gcc-3.4

---

### Post by adduds on 2005-11-27
just wondering how you came to know that so i can start picking up stuff like that, i guess it's mainly experience...thx very much tho

---

### Post by bluetoad on 2005-11-28
Just experience - no one is born with the knowledge :-).  I've been using Linux since 1994  and I've been a developer for some years before that...

gcc, make and other development packages are amongst the first things I add for things like this.

Going through this exercise will help you a lot.  When it comes to compiling most Open Source Software it is close to

1. ./configure --whateverOptions (look at the README and INSTALL files)
2. make
3. make install

So, even if you aren't a developer, after you've got this going you'll 

1. Have the tools installed for compiling a fair bit of the source code out there
2. Have been through the process and know what to do next time

So you'll be able to do it by "pushing buttons", hopefully ;-)  The only thing I needed to compile was ALSA on Hoary.  

If you are a developer in another environment it is probably worth doing a small "Hello, World"  tutorial where you end up using make to compile.  I've done a quick google and this looks like it would help [http://www.colorado.edu/ASEN/SrProjects/Class%20Presentations/C%20Programming.pdf](http://www.colorado.edu/ASEN/SrProjects/Class%20Presentations/C%20Programming.pdf)

Then you've been through the steps and understand.

The most important thing you are doing is asking.

---

### Post by adduds on 2005-11-28
Wow that's deadly c code, now is that C or C++ cause i did 2 years of C++ and i remember structs and enum, and #include<header.h> etc...

As for the driver install i got it done after the gcc-3.4 :) i also installed alot of the dvd codecs so i can watch dvd's now :).

But the reason I installed the ALSA drivers is too see if i could get my sound working, but it still doesn't....i dunno what to do now mang

I know alot of people have been having this problem, usually with the Intel 82801DB-ICH4 

Anyone fix this problem? and if so anyhelp would be appreciated?
Or 
Ideas in general

cheers/thx,
ad

---

