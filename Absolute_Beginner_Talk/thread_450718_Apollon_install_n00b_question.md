---
title: "Apollon install n00b question"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by stooker on 2007-05-21
Hey there,

I downloaded the file *apollon-installer-0.8.1.run* from the Apollon website.....but then?

It doesn't work like windows :oops: so a double click doesn't work.

How can I install it?

---

### Post by taurus on 2007-05-21
Open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 apollon-installer-0.8.1.run
sudo ./apollon-installer-0.8.1.run
```

---

### Post by stooker on 2007-05-21
Thanks it worked and started the install wizard....while installing and checking stuff it errored and gave me this log:

***** GiFT
***** Running configure (./configure --prefix=/usr/local)...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for sed... /bin/sed
checking for perl... /usr/bin/perl
checking for xsltproc... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for gethostbyname in -lnsl... yes
checking for socket in -lsocket... no
checking for opendir in -lmingwex... no
checking for inet_ntoa in -lbind... no
checking for openlog in -lbe... no
checking if -lws2_32 is needed... no
checking if -lwsock32 is needed... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking linux/limits.h usability... yes
checking linux/limits.h presence... yes
checking for linux/limits.h... yes
checking for stdint.h... (cached) yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for unistd.h... (cached) yes
checking for inttypes.h... (cached) yes
checking io.h usability... no
checking io.h presence... no
checking for io.h... no
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether byte ordering is bigendian... no
checking for an implementation of va_copy()... yes
checking for an implementation of __va_copy()... yes
checking whether va_lists can be copied by value... yes
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking for void *... yes
checking size of void *... 4
checking for uint8_t... yes
checking for int8_t... yes
checking for uint16_t... yes
checking for int16_t... yes
checking for uint32_t... yes
checking for int32_t... yes
checking for in_addr_t... yes
checking for in_port_t... yes
checking for pid_t... yes
checking for off_t... yes
checking for ssize_t... yes
checking for size_t... yes
checking for getopt... yes
checking for getopt_long... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for ftruncate... yes
checking for gettimeofday... yes
checking for madvise... yes
checking for memdup... no
checking for mkstemp... yes
checking for nice... yes
checking for select... yes
checking for poll... yes
checking for rmdir... yes
checking for signal... yes
checking for socket... yes
checking for socketpair... yes
checking for snprintf... yes
checking for _snprintf... no
checking for vsnprintf... yes
checking for _vsnprintf... no
checking for strcasecmp... yes
checking for strcspn... yes
checking for strlcat... no
checking for strlcpy... no
checking for strmove... no
checking for strpbrk... yes
checking for strspn... yes
checking for strtol... yes
checking for strtoul... yes
checking for unlink... yes
checking for lt_dlopen in -lltdl... no
 * configure: error:
 * *** Couldn't find ltdl library.  If it is installed in a non-standard
 * *** location, please supply --with-ltdl=DIR on the configure command line,
 * *** where `DIR' is the prefix where ltdl is installed (such as /usr,
 * *** /usr/local, or /usr/pkg).  If that doesn't work, check config.log.
 * 


Anybody know?

---

### Post by taurus on 2007-05-21
You need to open synaptic in System -> Administration and search for ltdl.  You probably need to install the development package for it, the one that comes with -dev.

---

### Post by stooker on 2007-05-22
I installed libguile-ltdl-1 // libltdl3 // ligltdl3-dev from the adept manager and then used your code again to install apollon, I got the following message:

***** FastTrack (Kazaa) plugin
***** Running configure (./configure --prefix=/usr/local)...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
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
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... no
checking for pkg-config... no
*** The pkg-config script could not be found. Make sure it is
*** in your path, or set the PKG_CONFIG environment variable
*** to the full path to pkg-config.
*** Or see [http://www.freedesktop.org/software/pkgconfig](http://www.freedesktop.org/software/pkgconfig) to get pkg-config.
 * configure: error: Library requirements (libgift >= 0.11.6 libgift < 0.12.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
***** Return value 1

Anybody?

---

### Post by stooker on 2007-05-22
Installed pkconfig from the adept menu, now the installation goes on for 13 minutes.

Hope it works !! :D

---

### Post by stooker on 2007-05-22
grrr.....after 37% the log errors with this message:

 * configure: error: Can't find X includes. Please check your installation and add the correct paths!
***** Return value 1

Can anybody plz help me?

---

### Post by taurus on 2007-05-22
It probably looks for xorg-dev.

```
sudo aptitude update
sudo aptitude install xorg-dev
```

---

### Post by stooker on 2007-05-22
It looked like going further, but it still stopped at 37% now with the following message:

checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
 * configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!
 * For more details about this problem, look at the end of config.log.
***** Return value 1

You know the answer again Taurus ?

---

### Post by taurus on 2007-05-22
Use synaptic and Search for qt.  You need the development package for qt.

---

### Post by stooker on 2007-05-22
I installed the following from synaptic:

- libpoppler-qt-dev
- libsmokeqt-dev

But still the same error on 37%.....

---

### Post by guysmiley25 on 2007-05-22
Why don't your just install apollon from the repositories?

```

sudo aptitude install gift apollon
gift-setup

```

Or if you want to connect to Ares and FastTrack as well.
```

sudo gedit /etc/sources.list

```

Add this to the file
```

deb http://apt.cerkinfo.be/ unstable main contrib
deb-src http://apt.cerkinfo.be/ unstable main contrib

```

Finally
```

sudo aptitude install gift libares-gift libfasttrack-gift apollon
gift-setup

```

---

### Post by stooker on 2007-05-22
Oke I tried it your way, after the last code I "entered" myself throught the process.....and then?

How can I start the programm?

*edit* typen " apollon"  in terminal worked fine :oops:

*edit again* it starts with a lot of errors and says it can't connect


X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
apollon: [virtual void ApollonPreferencesDialog::readConfig(bool)] init = true
stooker@stooker-desktop:~$
*** ERROR: Your setup is incomplete ***

You will need to run gift-setup and be sure that you read absolutely
every configuration option (no, really).  Some default configuration
values are considered illegal, and will raise this error message.  If you
suspect that you have configured giFT properly, consult the conf files in
/home/stooker/.giFT/ for diagnostic purposes.

If you are still having problems you should consult the QUICKSTART guide
available from the standard giFT distribution.


*** ERROR: Your setup is incomplete ***

You will need to run gift-setup and be sure that you read absolutely
every configuration option (no, really).  Some default configuration
values are considered illegal, and will raise this error message.  If you
suspect that you have configured giFT properly, consult the conf files in
/home/stooker/.giFT/ for diagnostic purposes.

If you are still having problems you should consult the QUICKSTART guide
available from the standard giFT distribution.


*** ERROR: Your setup is incomplete ***

You will need to run gift-setup and be sure that you read absolutely
every configuration option (no, really).  Some default configuration
values are considered illegal, and will raise this error message.  If you
suspect that you have configured giFT properly, consult the conf files in
/home/stooker/.giFT/ for diagnostic purposes.

If you are still having problems you should consult the QUICKSTART guide
available from the standard giFT distribution.

------------------

Why can't it just work the easy way :( 

Probably has something to do with the "entering" throught all the options, but I didn't knew all the answers. I'm used to windows and there is everything always enter ;)

---

### Post by guysmiley25 on 2007-05-23
When you first run gift-setup make sure you change the first option to a non zero value.

If you had done that the only other thing that it could be is that giftd is not running when you run apollon. So go

```

giftd -d
apollon

```

This will start gift in the background.

giFT is the program that does all the work and apollon is just a frontend for it. There are others avaible.

Let us know how you get on.

---

### Post by stooker on 2007-05-23
I reinstalled the whole thing and now inserted 1 instead of Zero....

After this started Apollon again and now it's trying to connect.

The statusbar under Info says " Trying to connect " While in the lower part of the screen it says "Connected". Searching gives 0 results on all, so I think I'm not connected.

* edit * IT says connected and "users: 1"  but only open ftp stands there. Hmmm....now it's connecting again.

---

### Post by stooker on 2007-05-23
It keeps connecting.....being connected.......connecting.....etc.

What can I do about that?

---

### Post by guysmiley25 on 2007-05-23
Sometimes it can take awhile to connect the first time.

Thanks to fang2415 to get Gnutella to connect try [this]("http://ubuntuforums.org/showpost.php?p=2241045&postcount=60").

OpenFT should connect eventually.

If you want to can try updating the node files. I'm working on a script at the moment that will automatically do this for your but for now goto [http://update.kceasy.com/update/]("http://update.kceasy.com/update/").

Then say you want to update the node file for Ares click on ares and then nodes. Download it and replace it with the one in ~/.giFT/Ares

Do the same with the other networks.

---

### Post by stooker on 2007-05-27
oke, it's weekend again....time to try get apollon started.

I deleted the OpenFTP item, cause I stayed connecting for a whole night. But how can I get the Open FTP, Gnutella etc...in Apollon and try to connect to at least 1 or two networks?

plz anybody, getting a bit tired from the fact that nothing works in once at Linux (and yes I'm a windows nerd, but still sticking to Kubuntu cause I don't want to give up withing 1 month).

---

### Post by stooker on 2007-05-27
I followed the link 2 posts ago and find all the nodes, but what can I do with it, or where do I have to install them?

* edit * Oke I went to 'Apollon configurations' -> Plugins and put the four connections in. But how can I update the nodes?

ps. they are all connecting, none of them gets connected.

---

