---
title: "Error compiling from source"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Battalion on 2008-03-10
Hi, I am new to using Kubuntu and am currently running Kubuntu 7.04 on my hdd.  

Please help me with the following problem i'm having. Whenever i try and compile a package from source, i get the following message in konsole:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.

Please help

---

### Post by hyper_ch on 2008-03-10
what does config.log say?

---

### Post by Battalion on 2008-03-10
I will copy the config.log file and post it tomorrow.  But i really don't understand the error because i'm a previous knoppix user and have never had problems compiling from source

---

### Post by Wolfygr on 2008-03-10
I get exactly the same error, im using Ubuntu 7.10 but i thought it would be better not to open a new thread. 
Thats my config.log 
```
## --------- ##
## Platform. ##
## --------- ##

hostname = xristos-desktop
uname -m = i686
uname -r = 2.6.22-14-generic
uname -s = Linux
uname -v = #1 SMP Tue Feb 12 07:42:25 UTC 2008

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


configure:2111: checking for a BSD-compatible install
configure:2167: result: /usr/bin/install -c
configure:2178: checking whether build environment is sane
configure:2221: result: yes
configure:2249: checking for a thread-safe mkdir -p
configure:2288: result: /bin/mkdir -p
configure:2301: checking for gawk
configure:2317: found /usr/bin/gawk
configure:2328: result: gawk
configure:2339: checking whether make sets $(MAKE)
configure:2360: result: yes
configure:2604: checking for gcc
configure:2620: found /usr/bin/gcc
configure:2631: result: gcc
configure:2869: checking for C compiler version
configure:2876: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2879: $? = 0
configure:2886: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:2889: $? = 0
configure:2896: gcc -V >&5
gcc: '-V' option must have argument
configure:2899: $? = 1
configure:2922: checking for C compiler default output file name
configure:2949: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2952: $? = 1
configure:2990: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "Conky"
| #define PACKAGE_TARNAME "conky"
| #define PACKAGE_VERSION "1.4.9"
| #define PACKAGE_STRING "Conky 1.4.9"
| #define PACKAGE_BUGREPORT "brenden1@users.sourceforge.net"
| #define PACKAGE "conky"
| #define VERSION "1.4.9"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2997: error: C compiler cannot create executables
See `config.log' for more details.

```

---

### Post by lloyd_b on 2008-03-10
Wolfygr, Batallion: Please run the following command:
```
sudo apt-get install build-essential
```
 
This will install everything that's required to have a working build system.

I can't tell anything from Batallion's errors, but Wolfygr's indicate that "crt1.o" is missing.  This file is part of the "libc6-dev" package, which will be installed by "build-essential".

Lloyd B.

---

### Post by hyper_ch on 2008-03-11
isn't conky in the repos?

---

### Post by Battalion on 2008-03-12
> **Wolfygr said:**
> I get exactly the same error, im using Ubuntu 7.10 but i thought it would be better not to open a new thread. 
Thats my config.log 

My config.log file is excatly the same.  So why doesn't this 'build essential' package come standard with Ubuntu?  This has caused me so many headaches

---

### Post by hyper_ch on 2008-03-12
> **Battalion said:**
> So why doesn't this 'build essential' package come standard with Ubuntu?

Why should it (considering Ubuntu is aimed at "human beings" and considering it's a binary distribution and not source-code based one)? Most people on Ubuntu won't try to compile - at least that's what I tend to think to.

---

### Post by Battalion on 2008-03-18
Thats true but somethings in life just need to be compiled from source and it should be included just in case some crazy guy like me wants to do things.  And "normal humans" want to play mp3 and watch movies out of the box and not have to download extra packages

---

### Post by hyper_ch on 2008-03-18
If you want to compile from source you should know the tools you need to do so.....

---

### Post by Battalion on 2008-03-18
I've never had to worry about such things in knoppix but i'm slowly adjusting to Ubuntu and will get to know all the necessary tools.

---

### Post by rickatnight11 on 2008-03-18
I am running into the same issue trying to compile everything needed for MonoDevelop.  I try to compile gtk-sharp-2.8.4 and get the same error about creating executables.  When I try to install build-essentials, however I get
```
 sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```
I have tried installing libc6-dev and g++ but both of them complain of the same thing; unmet dependencies.  I seem to be missing something.

EDIT: I have tried installing any dependencies it lists, and keep on getting more dependencies until I get to libc6 which it says is already installed.  I'm stumped.

---

### Post by Battalion on 2008-03-31
I have installed the build-essential package and i can now compile from source.  Thanks

---

