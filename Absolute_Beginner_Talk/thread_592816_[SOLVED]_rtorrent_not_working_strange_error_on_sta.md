---
title: "[SOLVED] rtorrent not working strange error on start up"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by pfwd.tech on 2007-10-26
This is becoming a pain in the neck.  Since the upgrade to Gusty I cannot get rtorrent to work. I have tried reinstalling it but I am still getting the same error which is:
```
rtorrent: symbol lookup error: rtorrent: undefined symbol: _ZN7torrent25set_max_download_unchokedEj

```
Does anyone know what this is?  I'm not over familiar with how rtorrent works (Dependices etc..) so I don't want to do anything unless I get some advice about it first i.e the forum.
Any Ideas on what I should do?

---

### Post by pfwd.tech on 2007-10-29
bump
Ive just removed libtorrent10, shutdown the machine and reinstalled rtorrent and im getting the same error.  Any help would be great 
heres the code:
```

:~$ sudo apt-get install rtorrent 
[sudo] password for ###:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libtorrent10
The following NEW packages will be installed
  libtorrent10 rtorrent
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 562kB of archives.
After unpacking 1470kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com gutsy/universe libtorrent10 0.11.4-1 [270kB]
Get: 2 http://gb.archive.ubuntu.com gutsy/universe rtorrent 0.7.4-2ubuntu2 [292kB]
Fetched 562kB in 0s (697kB/s) 
Selecting previously deselected package libtorrent10.
(Reading database ... 109881 files and directories currently installed.)
Unpacking libtorrent10 (from .../libtorrent10_0.11.4-1_i386.deb) ...
Selecting previously deselected package rtorrent.
Unpacking rtorrent (from .../rtorrent_0.7.4-2ubuntu2_i386.deb) ...
Setting up libtorrent10 (0.11.4-1) ...

Setting up rtorrent (0.7.4-2ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
~$ rtorrent
rtorrent: symbol lookup error: rtorrent: undefined symbol: _ZN7torrent25set_max_download_unchokedEj

```

---

### Post by pfwd.tech on 2007-10-29
Ah this is a headache .. that didnt work so i google more found this site tried it and still no joy
my code as is:
```
:/usr/local$ rm -rf rtorrent-0.7.1.tar.gz rtorrent-0.7.1 libtorrent-0.11.1.tar.gz libtorrent-0.11.1
:/usr/local$ cd
:~$ rtorrent
bash: /usr/bin/rtorrent: No such file or directory
:~$ sudo apt-get remove rtorrent libtorrent7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rtorrent is not installed, so not removed
E: Couldn't find package libtorrent7
:~$ sudo apt-get install build-essential libsigc++-2.0-dev pkg-config comerr-dev libcurl3-openssl-dev libidn11-dev libkadm55 libkrb5-dev libssl-dev zlib1g-dev libncurses5 libncurses5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libsigc++-2.0-dev is already the newest version.
pkg-config is already the newest version.
comerr-dev is already the newest version.
libncurses5 is already the newest version.
libncurses5-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libcurl3-openssl-dev: Depends: libcurl3 (= 7.15.5-1ubuntu2) but 7.16.4-2ubuntu1 is to be installed
E: Broken packages
:~$ cd /tmp
:/tmp$ wget http://libtorrent.rakshasa.no/downloads/libtorrent-0.11.1.tar.gz
--21:26:41--  http://libtorrent.rakshasa.no/downloads/libtorrent-0.11.1.tar.gz
           => `libtorrent-0.11.1.tar.gz'
Resolving libtorrent.rakshasa.no... 66.220.1.220
Connecting to libtorrent.rakshasa.no|66.220.1.220|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 477,557 (466K) [application/x-gzip]

100%[====================================>] 477,557      327.71K/s             

21:26:42 (326.88 KB/s) - `libtorrent-0.11.1.tar.gz' saved [477557/477557]

:/tmp$ wget http://libtorrent.rakshasa.no/downloads/rtorrent-0.7.1.tar.gz
--21:26:42--  http://libtorrent.rakshasa.no/downloads/rtorrent-0.7.1.tar.gz
           => `rtorrent-0.7.1.tar.gz'
Resolving libtorrent.rakshasa.no... 66.220.1.220
Connecting to libtorrent.rakshasa.no|66.220.1.220|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 414,447 (405K) [application/x-gzip]

100%[====================================>] 414,447      309.20K/s             

21:26:44 (308.47 KB/s) - `rtorrent-0.7.1.tar.gz' saved [414447/414447]

:/tmp$ 
:/tmp$ tar xfz libtorrent-0.11.1.tar.gz
:/tmp$ cd libtorrent-0.11.1
:/tmp/libtorrent-0.11.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking for fgrep... grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking the maximum length of command line arguments... 32768
checking for /usr/bin/ld option to reload object files... -r
checking how to recognise dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from  object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... 
checking whether byte ordering is bigendian... no
checking the byte alignment... none needed
checking for user-defined CXXFLAGS... default "-O2 -Wall"
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for epoll support... yes
checking for long... yes
checking size of long... 4
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking for statvfs... ok
checking if compiler supports __attribute__((visibility("default")))... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for OPENSSL... configure: error: Could not find openssl's crypto library
./configure: line 15612: exit: try: numeric argument required
./configure: line 15612: exit: try: numeric argument required
:/tmp/libtorrent-0.11.1$ make
make: *** No targets specified and no makefile found. Stop.
:/tmp/libtorrent-0.11.1$ sudo make install
make: *** No rule to make target `install'. Stop.
:/tmp/libtorrent-0.11.1$ 
:/tmp/libtorrent-0.11.1$ tar xfz rtorrent-0.7.1.tar.gz
tar: rtorrent-0.7.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
:/tmp/libtorrent-0.11.1$ cd rtorrent-0.7.1
bash: cd: rtorrent-0.7.1: No such file or directory
:/tmp/libtorrent-0.11.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking for fgrep... grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking the maximum length of command line arguments... 32768
checking for /usr/bin/ld option to reload object files... -r
checking how to recognise dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from  object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... 
checking whether byte ordering is bigendian... no
checking the byte alignment... none needed
checking for user-defined CXXFLAGS... default "-O2 -Wall"
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for epoll support... yes
checking for long... yes
checking size of long... 4
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking for statvfs... ok
checking if compiler supports __attribute__((visibility("default")))... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for OPENSSL... configure: error: Could not find openssl's crypto library
./configure: line 15612: exit: try: numeric argument required
./configure: line 15612: exit: try: numeric argument required
:/tmp/libtorrent-0.11.1$ make
make: *** No targets specified and no makefile found. Stop.
:/tmp/libtorrent-0.11.1$ sudo make install
make: *** No rule to make target `install'. Stop.
:/tmp/libtorrent-0.11.1$ sudo iptables -A INPUT -p tcp --dport 6890-6999 -j ACCEPT
iptables v1.3.6: invalid port/service `6890-6999' specified
Try `iptables -h' or 'iptables --help' for more information.
:/tmp/libtorrent-0.11.1$ cd
:~$ rtorrent
bash: /usr/bin/rtorrent: No such file or directory
:~$ 
```


i take it that I am missing chucks of packages.  Can anyone see what I need or what i should do to get rtorrent to work again

---

### Post by pfwd.tech on 2007-10-29
and now i have no sound!!

---

### Post by konsole on 2007-10-31
> **pfwd.tech said:**
> Ah this is a headache .. that didnt work so i google more found this site tried it and still no joy

i take it that I am missing chucks of packages.  Can anyone see what I need or what i should do to get rtorrent to work again

From your code, it appears that openssl and libcurl3-openssl-dev are either missing or broken. You'll need to fix these first.

Some other things to note:
Don't compile software in /tmp. Make a directory e.g. /home/src then chown it to your user account and use that to compile.
Visit this website [http://libtorrent.rakshasa.no](http://libtorrent.rakshasa.no) it has lot's of information.
Read the mailing list archives from the website.
Visit #libtorrent on Worldforge irc and ask there.

The answers are out there, the fun is in the finding.

---

### Post by pfwd.tech on 2007-11-01
Ok will take on board yout surrgestion about an src folder.  Why would i need to change from tmp .. what would the benifts be?
In the mean time i have done some hunting and i'm still coming up blank.
this is the code:
```

# Lets see what I can get

:~$ sudo apt-get install build-essential libsigc++-2.0-dev pkg-config comerr-dev libcurl3-openssl-dev libidn11-dev libkadm55 libkrb5-dev libssl-dev zlib1g-dev libncurses5 libncurses5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libsigc++-2.0-dev is already the newest version.
pkg-config is already the newest version.
comerr-dev is already the newest version.
libncurses5 is already the newest version.
libncurses5-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

# So libcurl3-openssl-dev can't be found due to oppenssl or libcurl3

The following packages have unmet dependencies.
  libcurl3-openssl-dev: Depends: libcurl3 (= 7.15.5-1ubuntu2) but 7.16.4-2ubuntu1 is to be installed
E: Broken packages
# I can't get openssl - Apparently its already there! 

:~$ sudo apt-get install open
Display all 675 possibilities? (y or n)
pete@pete:~$ sudo apt-get install openss
openssh-client  openssh-server  openssl         
pete@pete:~$ sudo apt-get install openssl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

#  I Can't get libcurl3-openssl-dev it needs libcurl3

:~$ sudo apt-get install libcurl3-openssl-dev 
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

The following packages have unmet dependencies.
  libcurl3-openssl-dev: Depends: libcurl3 (= 7.15.5-1ubuntu2) but 7.16.4-2ubuntu1 is to be installed
E: Broken packages

# I cant get libcurl3!! Apparently its already there!

:~$ sudo apt-get install libcurl3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcurl3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

# Im at a loss

```Aparently I have already got what is needed. hummm

---

### Post by pfwd.tech on 2007-11-02
Any help here would be grand.
I have tried getting all the dependency's for libcurl3 but I have all of them.  I'm new to this game so i could be overlooking something.

---

### Post by pfwd.tech on 2007-11-20
I found out that i was still using old Fesity repos. I removed these and reinstalled rtorrent and it works fine

---

