---
title: "Setting up a Dell 1450 -external USB wi-fi adapter"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by VidK on 2006-12-21
Ok.. new thread. I was successful in getting build-essential and alien installed and working. (Thanks to my helpers!)

Step 2 and the bigger issue is getting my Dell USB Wireless adapter (Model 1450) installed and working. The CDRom that came with the adapter has both the Linux and Win drivers for it. The WinXP drivers work fine in Windows (using the adapter now - so I know it's working). However, when I attept to use the Linux driver, it seems to install ok, but nothing is working.

I haven't been able to use the ndiswrapper because I haven't (after several attempts) been able to get ndiswrapper to install. I've tried using the Ubuntu 6.06 CD to install it and I get an error (view thread here):


[http://www.ubuntuforums.org/showthread.php?t=322094&page=2](http://www.ubuntuforums.org/showthread.php?t=322094&page=2)

and the beginning of the thread is here:

[http://www.ubuntuforums.org/showthread.php?t=322094](http://www.ubuntuforums.org/showthread.php?t=322094)

I have the Linux drivers and I think they look like they are installed properly. The Dell docs told me to d/l and install something called 'dkms', which I did. I ran 'dkms status' and, contrary to Dell's docs, no results were returned to indicate the status of the driver or the adapter. Why isn't the wi-fi adapter working? What's my next step?

David ](*,)

---

### Post by VidK on 2006-12-21
Hey Guys!

I've managed to get a little further on my own! But I wouldn't be this far without you!

I've managed to compile ndiswrapper and install the Windows driver for my adapter. I also have the Linux driver installed, but I have no idea if it's working or not. At least, with the ndiswrapper technique, I have some indication that Linux is detecting my driver and adapter.

BUT! It's still not working. Here's what I tried and the results! 

Please keep the help coming! We're almost there - I can FEEL it! And don't worry, this help will be deseminated by me to future Ubuntu users here on the forum. Your efforts WILL be repaid! I promise!

David :mrgreen: 


david@david-desktop:/media/sda4/temp/drivers/Dell 1450 Wireless USB Adapter$ ndiswrapper -i dellnic.inf
Installing dellnic
Unable to create directory /etc/ndiswrapper/dellnic.Make sure you are running as root
david@david-desktop:/media/sda4/temp/drivers/Dell 1450 Wireless USB Adapter$ sudo ndiswrapper -i dellnic.inf
Installing dellnic
david@david-desktop:/media/sda4/temp/drivers/Dell 1450 Wireless USB Adapter$ ndiswrapper -l
Installed ndis drivers:
dellnic         driver present, hardware present
david@david-desktop:/media/sda4/temp/drivers/Dell 1450 Wireless USB Adapter$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

david@david-desktop:/media/sda4/temp/drivers/Dell 1450 Wireless USB Adapter$ iwlist eth2 scan
eth2      No scan results

---

### Post by macogw on 2006-12-21
What's ifconfig say?

---

### Post by VidK on 2006-12-21
Here's what I get from ifconfig. I posted everything because I thought it might all be relevent. If I don't need to (ie. just post things relevent to eth2) let me know, ok? 

~Vid~


eth0      Link encap:Ethernet  HWaddr 00:13:72:CA:85:B5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth2      Link encap:Ethernet  HWaddr 00:14:A5:C7:E7:2B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2640 (2.5 KiB)  TX bytes:2640 (2.5 KiB)

---

### Post by macogw on 2006-12-21
Were you able to install network-manager-gnome and nm-applet?  It'd probably be another "crap...downloading without apt....dependencies....bah" thing, but that seems to work a LOT better than System > Administration > Networking

---

### Post by VidK on 2006-12-21
I did download NetworkManager but didn't install it out of fear that installing that too soon might mess things up. nm-applet? I don't know where to find that. Is it part of NetworkManager and should I try installing them?

(PS.. I downloaded NetworkManager from the GNOME project site as a TAR file. Not the package from Ubuntu packages site. The TAR has all the dependencies, right?)

---

### Post by macogw on 2006-12-21
Yes, install both network-manager-gnome and nm-applet.  nm-applet makes a drop down at the top of your screen to pick what wireless network you connect to.

---

### Post by VidK on 2006-12-21
Where do I get nm-applet? Is it part of the TAR file I downloaded from the NetworkManager site? Also, does that TAR file have all the NetworkManager dependencies?

---

### Post by VidK on 2006-12-21
ok.. I tried making the file and got several errors. (sorry, btw, I could've looked in the TAR file to see nm-applet was there). Here are the errors I got. GCC wasn't installed and I got an error for that. I managed to install that using Synaptic. But, still getting errors. I can prolly find 'gawk' ... but what about the other errors?

david@david-desktop:/media/sda4/temp/TarFiles/NetworkManager-0.6.4$ ./configure checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
david@david-desktop:/media/sda4/temp/TarFiles/NetworkManager-0.6.4$

---

### Post by macogw on 2006-12-22
tar?  network-manager-gnome and nm-applet are both debs!  [http://packages.ubuntu.com/edgy/net/network-manager-gnome](http://packages.ubuntu.com/edgy/net/network-manager-gnome)

---

### Post by jbutler12 on 2006-12-22
While graphic interfaces are neat and all, i find that with wireless they are much more hassle than they are worth.  First, lets see if your card is working properly.  If it is, then we can concentrate on testing your interface configurations.  If not, we have to look at your driver.  So lets rule things out one at a time using the command line.

Issue the command:

```
iwlist wlan2 scan
```

and post the results.  If this works, we know your card is working and we can move on to testing the interface using some iwconfig commands.

-John

---

### Post by VidK on 2006-12-22
I went to the website listed on that link you gave. They had all the files archived into one package so I used that. :) You can check the TAR file there. Should I go back and download all those deb files?? (please say no... please say no!)

I've gotten pretty far... I did the ./configure and it ran through a whole list of checks till it got to this one...

```
checking for XML::Parser... configure: error: XML::Parser perl module is require d for intltool
```

---

### Post by jbutler12 on 2006-12-22
Installing the graphic tools is useless without a working driver.  Please run

iwlist wlan2 scan

to make sure your driver is correctly installed and post the results.

---

### Post by VidK on 2006-12-22
ok... I did as you asked and here are the results. I also did an iwlist on eth2 (where the adapter is located), an iwconfig and an ndiswrapper -l. Ubuntu is 'seeing' my adapter and driver. It's just not connecting to anything. 


```
 

wlan0     Interface doesn't support scanning.

david@david-desktop:~$ iwlist eth2 scan
eth2      No scan results


david@david-desktop:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

david@david-desktop:/media/sda4/temp/drivers/Dell 1450 Wireless USB Adapter$ ndiswrapper -l
Installed ndis drivers:
dellnic         driver present, hardware present




```

---

### Post by jbutler12 on 2006-12-22
thats wierd that it would name it eth2.  Did you rename it yourself?

It isnt finding your wireless network, so working on the interface would be pointless until we get iwlist <interface> scan to bring up a list of networks.  Next thing to check: did you load the ndiswrapper module?  This is done by:

modprobe ndiswrapper

If you get no error, try to scan again with the module loaded, after verifying your interface name with iwconfig.  If you get an error on modprobe, post that error, if you dont get an error, please post the output of another iwlist scan and iwconfig.

-John

---

### Post by VidK on 2006-12-22
yes.. I had done the modprobe per the instructions ndiswrapper instructions. After I did it... sudo modprobe ndiswrapper .. it paused for a second then brought me to another prompt. No "modprobe successful" or anything. The iwconfig and iwlist are after I ran the modprobe.

---

### Post by VidK on 2006-12-22
I went to the GNOME NetworkAdapter project site and they had a TAR archive with (I thought) all the files I needed. Here's a copy of the config.log. I'll hit that link you posted in the thread and download all the .deb files and dependencies tommorow. It's 4am here *w00t* pulled an all-nighter! Time to get some Zzzzzzs.

```
 
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by NetworkManager configure 0.6.4, which was
generated by GNU Autoconf 2.60.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = david-desktop
uname -m = i686
uname -r = 2.6.15-26-386
uname -s = Linux
uname -v = #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
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
PATH: /usr/bin/X11
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2143: checking for a BSD-compatible install
configure:2199: result: /usr/bin/install -c
configure:2210: checking whether build environment is sane
configure:2253: result: yes
configure:2318: checking for gawk
configure:2334: found /usr/bin/gawk
configure:2345: result: gawk
configure:2356: checking whether make sets $(MAKE)
configure:2377: result: yes
configure:2561: checking whether to enable maintainer-specific portions of Makefiles
configure:2570: result: no
configure:2637: checking for gcc
configure:2653: found /usr/bin/gcc
configure:2664: result: gcc
configure:2902: checking for C compiler version
configure:2909: gcc --version >&5
gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2912: $? = 0
configure:2919: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
configure:2922: $? = 0
configure:2929: gcc -V >&5
gcc: '-V' option must have argument
configure:2932: $? = 1
configure:2955: checking for C compiler default output file name
configure:2982: gcc    conftest.c  >&5
configure:2985: $? = 0
configure:3031: result: a.out
configure:3036: checking whether the C compiler works
configure:3046: ./a.out
configure:3049: $? = 0
configure:3066: result: yes
configure:3073: checking whether we are cross compiling
configure:3075: result: no
configure:3078: checking for suffix of executables
configure:3085: gcc -o conftest    conftest.c  >&5
configure:3088: $? = 0
configure:3112: result: 
configure:3118: checking for suffix of object files
configure:3144: gcc -c   conftest.c >&5
configure:3147: $? = 0
configure:3170: result: o
configure:3174: checking whether we are using the GNU C compiler
configure:3203: gcc -c   conftest.c >&5
configure:3209: $? = 0
configure:3216: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:3219: $? = 0
configure:3226: test -s conftest.o
configure:3229: $? = 0
configure:3243: result: yes
configure:3248: checking whether gcc accepts -g
configure:3278: gcc -c -g  conftest.c >&5
configure:3284: $? = 0
configure:3291: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:3294: $? = 0
configure:3301: test -s conftest.o
configure:3304: $? = 0
configure:3434: result: yes
configure:3451: checking for gcc option to accept ISO C89
configure:3525: gcc  -c -g -O2  conftest.c >&5
configure:3531: $? = 0
configure:3538: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:3541: $? = 0
configure:3548: test -s conftest.o
configure:3551: $? = 0
configure:3571: result: none needed
configure:3600: checking for style of include used by make
configure:3628: result: GNU
configure:3656: checking dependency style of gcc
configure:3746: result: gcc3
configure:3764: checking whether gcc and cc understand -c and -o together
configure:3799: gcc -c conftest.c -o conftest2.o >&5
configure:3802: $? = 0
configure:3808: gcc -c conftest.c -o conftest2.o >&5
configure:3811: $? = 0
configure:3822: cc -c conftest.c >&5
configure:3825: $? = 0
configure:3833: cc -c conftest.c -o conftest2.o >&5
configure:3836: $? = 0
configure:3842: cc -c conftest.c -o conftest2.o >&5
configure:3845: $? = 0
configure:3863: result: yes
configure:3901: checking for a BSD-compatible install
configure:3957: result: /usr/bin/install -c
configure:4046: checking build system type
configure:4064: result: i686-pc-linux-gnu
configure:4086: checking host system type
configure:4101: result: i686-pc-linux-gnu
configure:4123: checking for a sed that does not truncate output
configure:4177: result: /bin/sed
configure:4180: checking for grep that handles long lines and -e
configure:4254: result: /bin/grep
configure:4259: checking for egrep
configure:4337: result: /bin/grep -E
configure:4353: checking for ld used by gcc
configure:4420: result: /usr/bin/ld
configure:4429: checking if the linker (/usr/bin/ld) is GNU ld
configure:4444: result: yes
configure:4449: checking for /usr/bin/ld option to reload object files
configure:4456: result: -r
configure:4474: checking for BSD-compatible nm
configure:4523: result: /usr/bin/nm -B
configure:4527: checking whether ln -s works
configure:4531: result: yes
configure:4538: checking how to recognise dependent libraries
configure:4714: result: pass_all
configure:4964: checking how to run the C preprocessor
configure:5004: gcc -E  conftest.c
configure:5010: $? = 0
configure:5048: gcc -E  conftest.c
conftest.c:10:28: error: ac_nonexistent.h: No such file or directory
configure:5054: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "NetworkManager"
| #define PACKAGE_TARNAME "NetworkManager"
| #define PACKAGE_VERSION "0.6.4"
| #define PACKAGE_STRING "NetworkManager 0.6.4"
| #define PACKAGE_BUGREPORT "dcbw@redhat.com"
| #define PACKAGE "NetworkManager"
| #define VERSION "0.6.4"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:5094: result: gcc -E
configure:5123: gcc -E  conftest.c
configure:5129: $? = 0
configure:5167: gcc -E  conftest.c
conftest.c:10:28: error: ac_nonexistent.h: No such file or directory
configure:5173: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "NetworkManager"
| #define PACKAGE_TARNAME "NetworkManager"
| #define PACKAGE_VERSION "0.6.4"
| #define PACKAGE_STRING "NetworkManager 0.6.4"
| #define PACKAGE_BUGREPORT "dcbw@redhat.com"
| #define PACKAGE "NetworkManager"
| #define VERSION "0.6.4"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:5218: checking for ANSI C header files
configure:5248: gcc -c -g -O2  conftest.c >&5
configure:5254: $? = 0
configure:5261: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5264: $? = 0
configure:5271: test -s conftest.o
configure:5274: $? = 0
configure:5370: gcc -o conftest -g -O2   conftest.c  >&5
configure:5373: $? = 0
configure:5379: ./conftest
configure:5382: $? = 0
configure:5399: result: yes
configure:5423: checking for sys/types.h
configure:5444: gcc -c -g -O2  conftest.c >&5
configure:5450: $? = 0
configure:5457: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5460: $? = 0
configure:5467: test -s conftest.o
configure:5470: $? = 0
configure:5483: result: yes
configure:5423: checking for sys/stat.h
configure:5444: gcc -c -g -O2  conftest.c >&5
configure:5450: $? = 0
configure:5457: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5460: $? = 0
configure:5467: test -s conftest.o
configure:5470: $? = 0
configure:5483: result: yes
configure:5423: checking for stdlib.h
configure:5444: gcc -c -g -O2  conftest.c >&5
configure:5450: $? = 0
configure:5457: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5460: $? = 0
configure:5467: test -s conftest.o
configure:5470: $? = 0
configure:5483: result: yes
configure:5423: checking for string.h
configure:5444: gcc -c -g -O2  conftest.c >&5
configure:5450: $? = 0
configure:5457: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5460: $? = 0
configure:5467: test -s conftest.o
configure:5470: $? = 0
configure:5483: result: yes
configure:5423: checking for memory.h
configure:5444: gcc -c -g -O2  conftest.c >&5
configure:5450: $? = 0
configure:5457: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5460: $? = 0
configure:5467: test -s conftest.o
configure:5470: $? = 0
configure:5483: result: yes
configure:5423: checking for strings.h
configure:5444: gcc -c -g -O2  conftest.c >&5
configure:5450: $? = 0
configure:5457: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5460: $? = 0
configure:5467: test -s conftest.o
configure:5470: $? = 0
configure:5483: result: yes
configure:5423: checking for inttypes.h
configure:5444: gcc -c -g -O2  conftest.c >&5
configure:5450: $? = 0
configure:5457: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5460: $? = 0
configure:5467: test -s conftest.o
configure:5470: $? = 0
configure:5483: result: yes
configure:5423: checking for stdint.h
configure:5444: gcc -c -g -O2  conftest.c >&5
configure:5450: $? = 0
configure:5457: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5460: $? = 0
configure:5467: test -s conftest.o
configure:5470: $? = 0
configure:5483: result: yes
configure:5423: checking for unistd.h
configure:5444: gcc -c -g -O2  conftest.c >&5
configure:5450: $? = 0
configure:5457: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5460: $? = 0
configure:5467: test -s conftest.o
configure:5470: $? = 0
configure:5483: result: yes
configure:5510: checking dlfcn.h usability
configure:5527: gcc -c -g -O2  conftest.c >&5
configure:5533: $? = 0
configure:5540: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:5543: $? = 0
configure:5550: test -s conftest.o
configure:5553: $? = 0
configure:5564: result: yes
configure:5568: checking dlfcn.h presence
configure:5583: gcc -E  conftest.c
configure:5589: $? = 0
configure:5610: result: yes
configure:5643: checking for dlfcn.h
configure:5651: result: yes
configure:5722: checking for g++
configure:5738: found /usr/bin/g++
configure:5749: result: g++
configure:5780: checking for C++ compiler version
configure:5787: g++ --version >&5
g++ (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:5790: $? = 0
configure:5797: g++ -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
configure:5800: $? = 0
configure:5807: g++ -V >&5
g++: '-V' option must have argument
configure:5810: $? = 1
configure:5813: checking whether we are using the GNU C++ compiler
configure:5842: g++ -c   conftest.cpp >&5
configure:5848: $? = 0
configure:5855: test -z "$ac_cxx_werror_flag" || test ! -s conftest.err
configure:5858: $? = 0
configure:5865: test -s conftest.o
configure:5868: $? = 0
configure:5882: result: yes
configure:5887: checking whether g++ accepts -g
configure:5917: g++ -c -g  conftest.cpp >&5
configure:5923: $? = 0
configure:5930: test -z "$ac_cxx_werror_flag" || test ! -s conftest.err
configure:5933: $? = 0
configure:5940: test -s conftest.o
configure:5943: $? = 0
configure:6073: result: yes
configure:6098: checking dependency style of g++
configure:6188: result: gcc3
configure:6215: checking how to run the C++ preprocessor
configure:6251: g++ -E  conftest.cpp
configure:6257: $? = 0
configure:6295: g++ -E  conftest.cpp
conftest.cpp:21:28: error: ac_nonexistent.h: No such file or directory
configure:6301: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "NetworkManager"
| #define PACKAGE_TARNAME "NetworkManager"
| #define PACKAGE_VERSION "0.6.4"
| #define PACKAGE_STRING "NetworkManager 0.6.4"
| #define PACKAGE_BUGREPORT "dcbw@redhat.com"
| #define PACKAGE "NetworkManager"
| #define VERSION "0.6.4"
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:6341: result: g++ -E
configure:6370: g++ -E  conftest.cpp
configure:6376: $? = 0
configure:6414: g++ -E  conftest.cpp
conftest.cpp:21:28: error: ac_nonexistent.h: No such file or directory
configure:6420: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "NetworkManager"
| #define PACKAGE_TARNAME "NetworkManager"
| #define PACKAGE_VERSION "0.6.4"
| #define PACKAGE_STRING "NetworkManager 0.6.4"
| #define PACKAGE_BUGREPORT "dcbw@redhat.com"
| #define PACKAGE "NetworkManager"
| #define VERSION "0.6.4"
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:6520: checking for g77
configure:6550: result: no
configure:6520: checking for f77
configure:6550: result: no
configure:6520: checking for xlf
configure:6550: result: no
configure:6520: checking for frt
configure:6550: result: no
configure:6520: checking for pgf77
configure:6550: result: no
configure:6520: checking for cf77
configure:6550: result: no
configure:6520: checking for fort77
configure:6550: result: no
configure:6520: checking for fl32
configure:6550: result: no
configure:6520: checking for af77
configure:6550: result: no
configure:6520: checking for f90
configure:6550: result: no
configure:6520: checking for xlf90
configure:6550: result: no
configure:6520: checking for pgf90
configure:6550: result: no
configure:6520: checking for pghpf
configure:6550: result: no
configure:6520: checking for epcf90
configure:6550: result: no
configure:6520: checking for gfortran
configure:6550: result: no
configure:6520: checking for g95
configure:6550: result: no
configure:6520: checking for f95
configure:6550: result: no
configure:6520: checking for fort
configure:6550: result: no
configure:6520: checking for xlf95
configure:6550: result: no
configure:6520: checking for ifort
configure:6550: result: no
configure:6520: checking for ifc
configure:6550: result: no
configure:6520: checking for efc
configure:6550: result: no
configure:6520: checking for pgf95
configure:6550: result: no
configure:6520: checking for lf95
configure:6550: result: no
configure:6520: checking for ftn
configure:6550: result: no
configure:6577: checking for Fortran 77 compiler version
configure:6584:  --version >&5
./configure: line 6585: --version: command not found
configure:6587: $? = 127
configure:6594:  -v >&5
./configure: line 6595: -v: command not found
configure:6597: $? = 127
configure:6604:  -V >&5
./configure: line 6605: -V: command not found
configure:6607: $? = 127
configure:6615: checking whether we are using the GNU Fortran 77 compiler
configure:6634:  -c  conftest.F >&5
./configure: line 6635: -c: command not found
configure:6640: $? = 127
configure: failed program was:
|       program main
| #ifndef __GNUC__
|        choke me
| #endif
| 
|       end
configure:6674: result: no
configure:6680: checking whether  accepts -g
configure:6697:  -c -g conftest.f >&5
./configure: line 6698: -c: command not found
configure:6703: $? = 127
configure: failed program was:
|       program main
| 
|       end
configure:6736: result: no
configure:6766: checking the maximum length of command line arguments
configure:6875: result: 32768
configure:6886: checking command to parse /usr/bin/nm -B output from gcc object
configure:6991: gcc -c -g -O2  conftest.c >&5
configure:6994: $? = 0
configure:6998: /usr/bin/nm -B conftest.o \| sed -n -e 's/^.*[ 	]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ 	][ 	]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' \> conftest.nm
configure:7001: $? = 0
configure:7053: gcc -o conftest -g -O2   conftest.c conftstm.o >&5
configure:7056: $? = 0
configure:7094: result: ok
configure:7098: checking for objdir
configure:7113: result: .libs
configure:7205: checking for ar
configure:7221: found /usr/bin/ar
configure:7232: result: ar
configure:7301: checking for ranlib
configure:7317: found /usr/bin/ranlib
configure:7328: result: ranlib
configure:7397: checking for strip
configure:7413: found /usr/bin/strip
configure:7424: result: strip
configure:7710: checking if gcc supports -fno-rtti -fno-exceptions
configure:7728: gcc -c -g -O2  -fno-rtti -fno-exceptions conftest.c >&5
cc1: warning: command line option "-fno-rtti" is valid for C++/ObjC++ but not for C
configure:7732: $? = 0
configure:7745: result: no
configure:7760: checking for gcc option to produce PIC
configure:7970: result: -fPIC
configure:7978: checking if gcc PIC flag -fPIC works
configure:7996: gcc -c -g -O2  -fPIC -DPIC conftest.c >&5
configure:8000: $? = 0
configure:8013: result: yes
configure:8041: checking if gcc static flag -static works
configure:8069: result: yes
configure:8079: checking if gcc supports -c -o file.o
configure:8100: gcc -c -g -O2  -o out/conftest2.o conftest.c >&5
configure:8104: $? = 0
configure:8126: result: yes
configure:8152: checking whether the gcc linker (/usr/bin/ld) supports shared libraries
configure:9138: result: yes
configure:9159: checking whether -lc should be explicitly linked in
configure:9164: gcc -c -g -O2  conftest.c >&5
configure:9167: $? = 0
configure:9182: gcc -shared conftest.o  -v -Wl,-soname -Wl,conftest -o conftest 2\>\&1 \| grep  -lc  \>/dev/null 2\>\&1
configure:9185: $? = 0
configure:9197: result: no
configure:9205: checking dynamic linker characteristics
configure:9793: result: GNU/Linux ld.so
configure:9802: checking how to hardcode library paths into programs
configure:9827: result: immediate
configure:9841: checking whether stripping libraries is possible
configure:9846: result: yes
configure:10759: checking if libtool supports shared libraries
configure:10761: result: yes
configure:10764: checking whether to build shared libraries
configure:10785: result: yes
configure:10788: checking whether to build static libraries
configure:10792: result: yes
configure:10884: creating libtool
configure:11472: checking for ld used by g++
configure:11539: result: /usr/bin/ld
configure:11548: checking if the linker (/usr/bin/ld) is GNU ld
configure:11563: result: yes
configure:11614: checking whether the g++ linker (/usr/bin/ld) supports shared libraries
configure:12580: result: yes
configure:12598: g++ -c -g -O2  conftest.cpp >&5
configure:12601: $? = 0
configure:12720: checking for g++ option to produce PIC
configure:12994: result: -fPIC
configure:13002: checking if g++ PIC flag -fPIC works
configure:13020: g++ -c -g -O2  -fPIC -DPIC conftest.cpp >&5
configure:13024: $? = 0
configure:13037: result: yes
configure:13065: checking if g++ static flag -static works
configure:13093: result: yes
configure:13103: checking if g++ supports -c -o file.o
configure:13124: g++ -c -g -O2  -o out/conftest2.o conftest.cpp >&5
configure:13128: $? = 0
configure:13150: result: yes
configure:13176: checking whether the g++ linker (/usr/bin/ld) supports shared libraries
configure:13201: result: yes
configure:13268: checking dynamic linker characteristics
configure:13856: result: GNU/Linux ld.so
configure:13865: checking how to hardcode library paths into programs
configure:13890: result: immediate
configure:20095: checking for ANSI C header files
configure:20276: result: yes
configure:20306: checking fcntl.h usability
configure:20323: gcc -c -g -O2  conftest.c >&5
configure:20329: $? = 0
configure:20336: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20339: $? = 0
configure:20346: test -s conftest.o
configure:20349: $? = 0
configure:20360: result: yes
configure:20364: checking fcntl.h presence
configure:20379: gcc -E  conftest.c
configure:20385: $? = 0
configure:20406: result: yes
configure:20439: checking for fcntl.h
configure:20447: result: yes
configure:20306: checking paths.h usability
configure:20323: gcc -c -g -O2  conftest.c >&5
configure:20329: $? = 0
configure:20336: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20339: $? = 0
configure:20346: test -s conftest.o
configure:20349: $? = 0
configure:20360: result: yes
configure:20364: checking paths.h presence
configure:20379: gcc -E  conftest.c
configure:20385: $? = 0
configure:20406: result: yes
configure:20439: checking for paths.h
configure:20447: result: yes
configure:20306: checking sys/ioctl.h usability
configure:20323: gcc -c -g -O2  conftest.c >&5
configure:20329: $? = 0
configure:20336: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20339: $? = 0
configure:20346: test -s conftest.o
configure:20349: $? = 0
configure:20360: result: yes
configure:20364: checking sys/ioctl.h presence
configure:20379: gcc -E  conftest.c
configure:20385: $? = 0
configure:20406: result: yes
configure:20439: checking for sys/ioctl.h
configure:20447: result: yes
configure:20306: checking sys/time.h usability
configure:20323: gcc -c -g -O2  conftest.c >&5
configure:20329: $? = 0
configure:20336: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20339: $? = 0
configure:20346: test -s conftest.o
configure:20349: $? = 0
configure:20360: result: yes
configure:20364: checking sys/time.h presence
configure:20379: gcc -E  conftest.c
configure:20385: $? = 0
configure:20406: result: yes
configure:20439: checking for sys/time.h
configure:20447: result: yes
configure:20306: checking syslog.h usability
configure:20323: gcc -c -g -O2  conftest.c >&5
configure:20329: $? = 0
configure:20336: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20339: $? = 0
configure:20346: test -s conftest.o
configure:20349: $? = 0
configure:20360: result: yes
configure:20364: checking syslog.h presence
configure:20379: gcc -E  conftest.c
configure:20385: $? = 0
configure:20406: result: yes
configure:20439: checking for syslog.h
configure:20447: result: yes
configure:20296: checking for unistd.h
configure:20302: result: yes
configure:20461: checking for mode_t
configure:20491: gcc -c -g -O2  conftest.c >&5
configure:20497: $? = 0
configure:20504: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20507: $? = 0
configure:20514: test -s conftest.o
configure:20517: $? = 0
configure:20529: result: yes
configure:20541: checking for pid_t
configure:20571: gcc -c -g -O2  conftest.c >&5
configure:20577: $? = 0
configure:20584: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20587: $? = 0
configure:20594: test -s conftest.o
configure:20597: $? = 0
configure:20609: result: yes
configure:20621: checking whether time.h and sys/time.h may both be included
configure:20651: gcc -c -g -O2  conftest.c >&5
configure:20657: $? = 0
configure:20664: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20667: $? = 0
configure:20674: test -s conftest.o
configure:20677: $? = 0
configure:20689: result: yes
configure:20701: checking whether gcc needs -traditional
configure:20743: result: no
configure:20750: checking for working memcmp
configure:20803: gcc -o conftest -g -O2   conftest.c  >&5
configure:20806: $? = 0
configure:20812: ./conftest
configure:20815: $? = 0
configure:20831: result: yes
configure:20846: checking for select
configure:20902: gcc -o conftest -g -O2   conftest.c  >&5
configure:20908: $? = 0
configure:20915: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20918: $? = 0
configure:20925: test -s conftest
configure:20928: $? = 0
configure:20942: result: yes
configure:20846: checking for socket
configure:20902: gcc -o conftest -g -O2   conftest.c  >&5
configure:20908: $? = 0
configure:20915: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20918: $? = 0
configure:20925: test -s conftest
configure:20928: $? = 0
configure:20942: result: yes
configure:20846: checking for uname
configure:20902: gcc -o conftest -g -O2   conftest.c  >&5
configure:20908: $? = 0
configure:20915: test -z "$ac_c_werror_flag" || test ! -s conftest.err
configure:20918: $? = 0
configure:20925: test -s conftest
configure:20928: $? = 0
configure:20942: result: yes
configure:20981: checking for intltool >= 0.27.2
configure:20991: result: 0.34.1 found
configure:21048: checking for perl
configure:21066: found /usr/bin/perl
configure:21078: result: /usr/bin/perl
configure:21097: checking for XML::Parser
configure:21103: error: XML::Parser perl module is required for intltool

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_cxx_compiler_gnu=yes
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_DBUS_CFLAGS_set=
ac_cv_env_DBUS_CFLAGS_value=
ac_cv_env_DBUS_LIBS_set=
ac_cv_env_DBUS_LIBS_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_GCONF_CFLAGS_set=
ac_cv_env_GCONF_CFLAGS_value=
ac_cv_env_GCONF_LIBS_set=
ac_cv_env_GCONF_LIBS_value=
ac_cv_env_GDK_PIXBUF_CFLAGS_set=
ac_cv_env_GDK_PIXBUF_CFLAGS_value=
ac_cv_env_GDK_PIXBUF_LIBS_set=
ac_cv_env_GDK_PIXBUF_LIBS_value=
ac_cv_env_GLADE_CFLAGS_set=
ac_cv_env_GLADE_CFLAGS_value=
ac_cv_env_GLADE_LIBS_set=
ac_cv_env_GLADE_LIBS_value=
ac_cv_env_GLIB_CFLAGS_set=
ac_cv_env_GLIB_CFLAGS_value=
ac_cv_env_GLIB_LIBS_set=
ac_cv_env_GLIB_LIBS_value=
ac_cv_env_GMODULE_CFLAGS_set=
ac_cv_env_GMODULE_CFLAGS_value=
ac_cv_env_GMODULE_LIBS_set=
ac_cv_env_GMODULE_LIBS_value=
ac_cv_env_GNOME_KEYRING_CFLAGS_set=
ac_cv_env_GNOME_KEYRING_CFLAGS_value=
ac_cv_env_GNOME_KEYRING_LIBS_set=
ac_cv_env_GNOME_KEYRING_LIBS_value=
ac_cv_env_GTHREAD_CFLAGS_set=
ac_cv_env_GTHREAD_CFLAGS_value=
ac_cv_env_GTHREAD_LIBS_set=
ac_cv_env_GTHREAD_LIBS_value=
ac_cv_env_GTK_CFLAGS_set=
ac_cv_env_GTK_CFLAGS_value=
ac_cv_env_GTK_LIBS_set=
ac_cv_env_GTK_LIBS_value=
ac_cv_env_HAL_CFLAGS_set=
ac_cv_env_HAL_CFLAGS_value=
ac_cv_env_HAL_LIBS_set=
ac_cv_env_HAL_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBGNOMEUI_CFLAGS_set=
ac_cv_env_LIBGNOMEUI_CFLAGS_value=
ac_cv_env_LIBGNOMEUI_LIBS_set=
ac_cv_env_LIBGNOMEUI_LIBS_value=
ac_cv_env_LIBNL_CFLAGS_set=
ac_cv_env_LIBNL_CFLAGS_value=
ac_cv_env_LIBNL_LIBS_set=
ac_cv_env_LIBNL_LIBS_value=
ac_cv_env_NOTIFY_CFLAGS_set=
ac_cv_env_NOTIFY_CFLAGS_value=
ac_cv_env_NOTIFY_LIBS_set=
ac_cv_env_NOTIFY_LIBS_value=
ac_cv_env_PANEL_APPLET_CFLAGS_set=
ac_cv_env_PANEL_APPLET_CFLAGS_value=
ac_cv_env_PANEL_APPLET_LIBS_set=
ac_cv_env_PANEL_APPLET_LIBS_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_f77_compiler_gnu=no
ac_cv_func_memcmp_working=yes
ac_cv_func_select=yes
ac_cv_func_socket=yes
ac_cv_func_uname=yes
ac_cv_header_dlfcn_h=yes
ac_cv_header_fcntl_h=yes
ac_cv_header_inttypes_h=yes
ac_cv_header_memory_h=yes
ac_cv_header_paths_h=yes
ac_cv_header_stdc=yes
ac_cv_header_stdint_h=yes
ac_cv_header_stdlib_h=yes
ac_cv_header_string_h=yes
ac_cv_header_strings_h=yes
ac_cv_header_sys_ioctl_h=yes
ac_cv_header_sys_stat_h=yes
ac_cv_header_sys_time_h=yes
ac_cv_header_sys_types_h=yes
ac_cv_header_syslog_h=yes
ac_cv_header_time=yes
ac_cv_header_unistd_h=yes
ac_cv_host=i686-pc-linux-gnu
ac_cv_objext=o
ac_cv_path_EGREP='/bin/grep -E'
ac_cv_path_GREP=/bin/grep
ac_cv_path_INTLTOOL_PERL=/usr/bin/perl
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=gawk
ac_cv_prog_CPP='gcc -E'
ac_cv_prog_CXXCPP='g++ -E'
ac_cv_prog_ac_ct_AR=ar
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_CXX=g++
ac_cv_prog_ac_ct_RANLIB=ranlib
ac_cv_prog_ac_ct_STRIP=strip
ac_cv_prog_cc_c89=
ac_cv_prog_cc_g=yes
ac_cv_prog_cc_gcc_c_o=yes
ac_cv_prog_cxx_g=yes
ac_cv_prog_f77_g=no
ac_cv_prog_gcc_traditional=no
ac_cv_prog_make_make_set=yes
ac_cv_type_mode_t=yes
ac_cv_type_pid_t=yes
am_cv_CC_dependencies_compiler_type=gcc3
am_cv_CXX_dependencies_compiler_type=gcc3
lt_cv_deplibs_check_method=pass_all
lt_cv_file_magic_cmd='$MAGIC_CMD'
lt_cv_file_magic_test_file=
lt_cv_ld_reload_flag=-r
lt_cv_objdir=.libs
lt_cv_path_LD=/usr/bin/ld
lt_cv_path_LDCXX=/usr/bin/ld
lt_cv_path_NM='/usr/bin/nm -B'
lt_cv_path_SED=/bin/sed
lt_cv_prog_compiler_c_o=yes
lt_cv_prog_compiler_c_o_CXX=yes
lt_cv_prog_compiler_rtti_exceptions=no
lt_cv_prog_gnu_ld=yes
lt_cv_prog_gnu_ldcxx=yes
lt_cv_sys_global_symbol_pipe='sed -n -e '\''s/^.*[ 	]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ 	][ 	]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p'\'''
lt_cv_sys_global_symbol_to_c_name_address='sed -n -e '\''s/^: \([^ ]*\) $/  {\"\1\", (lt_ptr) 0},/p'\'' -e '\''s/^[BCDEGRST] \([^ ]*\) \([^ ]*\)$/  {"\2", (lt_ptr) \&\2},/p'\'''
lt_cv_sys_global_symbol_to_cdecl='sed -n -e '\''s/^. .* \(.*\)$/extern int \1;/p'\'''
lt_cv_sys_max_cmd_len=32768
lt_lt_cv_prog_compiler_c_o='"yes"'
lt_lt_cv_prog_compiler_c_o_CXX='"yes"'
lt_lt_cv_sys_global_symbol_pipe='"sed -n -e '\''s/^.*[ 	]\\([ABCDGIRSTW][ABCDGIRSTW]*\\)[ 	][ 	]*\\([_A-Za-z][_A-Za-z0-9]*\\)\$/\\1 \\2 \\2/p'\''"'
lt_lt_cv_sys_global_symbol_to_c_name_address='"sed -n -e '\''s/^: \\([^ ]*\\) \$/  {\\\"\\1\\\", (lt_ptr) 0},/p'\'' -e '\''s/^[BCDEGRST] \\([^ ]*\\) \\([^ ]*\\)\$/  {\"\\2\", (lt_ptr) \\&\\2},/p'\''"'
lt_lt_cv_sys_global_symbol_to_cdecl='"sed -n -e '\''s/^. .* \\(.*\\)\$/extern int \\1;/p'\''"'

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /media/sda4/temp/TarFiles/NetworkManager-0.6.4/missing --run aclocal-1.9'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /media/sda4/temp/TarFiles/NetworkManager-0.6.4/missing --run tar'
AR='ar'
AUTOCONF='${SHELL} /media/sda4/temp/TarFiles/NetworkManager-0.6.4/missing --run autoconf'
AUTOHEADER='${SHELL} /media/sda4/temp/TarFiles/NetworkManager-0.6.4/missing --run autoheader'
AUTOMAKE='${SHELL} /media/sda4/temp/TarFiles/NetworkManager-0.6.4/missing --run automake-1.9'
AWK='gawk'
CATALOGS=''
CATOBJEXT=''
CC='gcc'
CCDEPMODE='depmode=gcc3'
CFLAGS='-g -O2'
CPP='gcc -E'
CPPFLAGS=''
CXX='g++'
CXXCPP='g++ -E'
CXXDEPMODE='depmode=gcc3'
CXXFLAGS='-g -O2'
CYGPATH_W='echo'
DATADIRNAME=''
DBUS_CFLAGS=''
DBUS_LIBS=''
DBUS_SYS_DIR=''
DEFS=''
DEPDIR='.deps'
DHCDBD_BINARY_PATH=''
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='/bin/grep -E'
EXEEXT=''
EXPANDED_BINDIR=''
F77=''
FFLAGS=''
GCONF_CFLAGS=''
GCONF_LIBS=''
GDK_PIXBUF_CFLAGS=''
GDK_PIXBUF_LIBS=''
GETTEXT_PACKAGE='NetworkManager'
GLADE_CFLAGS=''
GLADE_LIBS=''
GLIB_CFLAGS=''
GLIB_LIBS=''
GMODULE_CFLAGS=''
GMODULE_LIBS=''
GMOFILES=''
GMSGFMT=''
GNOME_KEYRING_CFLAGS=''
GNOME_KEYRING_LIBS=''
GREP='/bin/grep'
GTHREAD_CFLAGS=''
GTHREAD_LIBS=''
GTK_CFLAGS=''
GTK_LIBS=''
HAL_CFLAGS=''
HAL_LIBS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
INSTOBJEXT=''
INTLLIBS=''
INTLTOOL_CAVES_RULE='%.caves:     %.caves.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_DESKTOP_RULE='%.desktop:   %.desktop.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'




```

.... continued on next post...

---

### Post by VidK on 2006-12-22
```


INTLTOOL_DIRECTORY_RULE='%.directory: %.directory.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_EXTRACT='$(top_builddir)/intltool-extract'
INTLTOOL_ICONV=''
INTLTOOL_KBD_RULE='%.kbd:       %.kbd.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -m -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_KEYS_RULE='%.keys:      %.keys.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -k -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_MERGE='$(top_builddir)/intltool-merge'
INTLTOOL_MSGFMT=''
INTLTOOL_MSGMERGE=''
INTLTOOL_OAF_RULE='%.oaf:       %.oaf.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -p $(top_srcdir)/po $< $@'
INTLTOOL_PERL='/usr/bin/perl'
INTLTOOL_PONG_RULE='%.pong:      %.pong.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_PROP_RULE='%.prop:      %.prop.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SCHEMAS_RULE='%.schemas:   %.schemas.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -s -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SERVER_RULE='%.server:    %.server.in    $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SHEET_RULE='%.sheet:     %.sheet.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SOUNDLIST_RULE='%.soundlist: %.soundlist.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_THEME_RULE='%.theme:     %.theme.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_UI_RULE='%.ui:        %.ui.in        $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_UPDATE='$(top_builddir)/intltool-update'
INTLTOOL_XAM_RULE='%.xam:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_XGETTEXT=''
INTLTOOL_XML_NOMERGE_RULE='%.xml:       %.xml.in       $(INTLTOOL_MERGE) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u /tmp $< $@'
INTLTOOL_XML_RULE='%.xml:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
IWLIB=''
LDFLAGS=''
LIBGCRYPT_CFLAGS=''
LIBGCRYPT_CONFIG=''
LIBGCRYPT_LIBS=''
LIBGNOMEUI_CFLAGS=''
LIBGNOMEUI_LIBS=''
LIBNL_CFLAGS=''
LIBNL_LIBS=''
LIBOBJS=''
LIBS=''
LIBTOOL='$(SHELL) $(top_builddir)/libtool'
LN_S='ln -s'
LTLIBOBJS=''
MAINT='#'
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE='#'
MAKEINFO='${SHELL} /media/sda4/temp/TarFiles/NetworkManager-0.6.4/missing --run makeinfo'
MSGFMT=''
NOTIFY_CFLAGS=''
NOTIFY_LIBS=''
OBJEXT='o'
PACKAGE='NetworkManager'
PACKAGE_BUGREPORT='dcbw@redhat.com'
PACKAGE_NAME='NetworkManager'
PACKAGE_STRING='NetworkManager 0.6.4'
PACKAGE_TARNAME='NetworkManager'
PACKAGE_VERSION='0.6.4'
PANEL_APPLET_CFLAGS=''
PANEL_APPLET_LIBS=''
PATH_SEPARATOR=':'
PKG_CONFIG=''
POFILES=''
POSUB=''
PO_IN_DATADIR_FALSE=''
PO_IN_DATADIR_TRUE=''
RANLIB='ranlib'
SET_MAKE=''
SHELL='/bin/sh'
STRIP='strip'
TARGET_ARCH_FALSE=''
TARGET_ARCH_TRUE=''
TARGET_DEBIAN_FALSE=''
TARGET_DEBIAN_TRUE=''
TARGET_GENTOO_FALSE=''
TARGET_GENTOO_TRUE=''
TARGET_REDHAT_FALSE=''
TARGET_REDHAT_TRUE=''
TARGET_SLACKWARE_FALSE=''
TARGET_SLACKWARE_TRUE=''
TARGET_SUSE_FALSE=''
TARGET_SUSE_TRUE=''
USE_NLS=''
VERSION='0.6.4'
WITH_GCRYPT_FALSE=''
WITH_GCRYPT_TRUE=''
WITH_GNOME_FALSE='#'
WITH_GNOME_TRUE=''
WITH_NOTIFY_FALSE=''
WITH_NOTIFY_TRUE=''
WPA_SUPPLICANT_BINARY_PATH=''
XGETTEXT=''
ac_ct_CC='gcc'
ac_ct_CXX='g++'
ac_ct_F77=''
am__fastdepCC_FALSE='#'
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE='#'
am__fastdepCXX_TRUE=''
am__include='include'
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='/media/sda4/temp/TarFiles/NetworkManager-0.6.4/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='mkdir -p --'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME "NetworkManager"
#define PACKAGE_TARNAME "NetworkManager"
#define PACKAGE_VERSION "0.6.4"
#define PACKAGE_STRING "NetworkManager 0.6.4"
#define PACKAGE_BUGREPORT "dcbw@redhat.com"
#define PACKAGE "NetworkManager"
#define VERSION "0.6.4"
#define STDC_HEADERS 1
#define HAVE_SYS_TYPES_H 1
#define HAVE_SYS_STAT_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STRING_H 1
#define HAVE_MEMORY_H 1
#define HAVE_STRINGS_H 1
#define HAVE_INTTYPES_H 1
#define HAVE_STDINT_H 1
#define HAVE_UNISTD_H 1
#define HAVE_DLFCN_H 1
#define STDC_HEADERS 1
#define HAVE_FCNTL_H 1
#define HAVE_PATHS_H 1
#define HAVE_SYS_IOCTL_H 1
#define HAVE_SYS_TIME_H 1
#define HAVE_SYSLOG_H 1
#define HAVE_UNISTD_H 1
#define TIME_WITH_SYS_TIME 1
#define HAVE_SELECT 1
#define HAVE_SOCKET 1
#define HAVE_UNAME 1
#define GETTEXT_PACKAGE "NetworkManager"

configure: exit 1


```

---

### Post by struva92 on 2006-12-24
I was having the same problems with the Dell 1450 USB 2.0 adapter on Edgy Eft, and just got it to work. I am on a Dell Dimension 5150.

I noticed that even after loading the ndiswrapper module, whenever I replugged in my adapter and did "tail /var/log/messages" that the kernel was preferring the islusb driver for the adapter and getting nowhere. So I added "blacklist islusb" to the end of the blacklist file in /etc/modprobe.d.  Then the kernel would not load islusb as the driver, but instead would load islsm_usb. So I added "blacklist islsm_usb" to the blacklist as well. Next time I replugged in the adapter it (finally) decided to load ndiswrapper.

At that point I could do "iwlist scan" OK, and then I just had to set up the essid, key ,etc. and put ndiswrapper in /etc/modules so it loaded during boot. Now it works!

If there is a more elegant way to get the kernel to prefer ndiswrapper to islusb and islsm_usb without blacklisting them, I would like to know.

---

