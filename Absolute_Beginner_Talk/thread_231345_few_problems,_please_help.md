---
title: "few problems, please help"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by zorro26 on 2006-08-07
Hi,
i have been playing round with Ubuntu for two months now, finally i have formatted my hard drive and just installed Ubuntu. i am still having few problems, can someone please help me:

1)[/COLOR]i tried the how to install things link([http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)) but i still cannot install most of the packages. when i try tar.bz2 or tar.gz i get following error

kal@kal-desktop:~$ sudo -i
root@kal-desktop:~# cd /home/kal/Desktop/glob2-0.8.21
root@kal-desktop:/home/kal/Desktop/glob2-0.8.21# ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for working alloca.h... yes
checking for alloca... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for string.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for gzdopen in -lz... yes
checking speex/speex.h usability... yes
checking speex/speex.h presence... yes
checking for speex/speex.h... yes
checking speex.h usability... no
checking speex.h presence... no
checking for speex.h... no
checking for speex_encoder_init in -lspeex... yes
checking for sdl-config... /usr/local/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking SDL_image.h usability... yes
checking SDL_image.h presence... yes
checking for SDL_image.h... yes
checking SDL_net.h usability... no
checking SDL_net.h presence... no
checking for SDL_net.h... no
configure: error: *** SDL_net headers not found !
root@kal-desktop:/home/kal/Desktop/glob2-0.8.21# make
make: *** No targets specified and no makefile found.  Stop.
root@kal-desktop:/home/kal/Desktop/glob2-0.8.21# make install
make: *** No rule to make target `install'.  Stop.
root@kal-desktop:/home/kal/Desktop/glob2-0.8.21# /home/kal/Desktop/glob2-0.8.21/ install-sh
/home/kal/Desktop/glob2-0.8.21/install-sh: no input file specified.
root@kal-desktop:/home/kal/Desktop/glob2-0.8.21# make check
make: *** No rule to make target `check'.  Stop.
root@kal-desktop:/home/kal/Desktop/glob2-0.8.21#

note: when i extract the folder i alwayts check readme or istall file and it ask me to do the same, ./configure, make and than make install.

2)when i try to convert rpm package to deb, i get following error:

kal@kal-desktop:~$ sudo -i
Password:
root@kal-desktop:~# alien /home/kal/Desktop/dark-oberon-1.0.2rc1-1polinux.i586.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/dark-oberon
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find path for libfmod-3.74.1.so
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx from: /usr/lib32/libGL.so.1
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx to: /usr/lib32/fglrx/libGL.so.1.xlibmesa
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libGLU (soname 1, path /usr/lib32/libGLU.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXxf86vm (soname 1, path /usr/lib32/libXxf86vm.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libfmod.so.3.74.1)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libfmod (soname 3.74.1, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path /usr/lib32/libstdc++.so.5, dependency field Depends)dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: dark-oberon-1.0.2rc1: No such file or directory
root@kal-desktop:~#

3)when i try to add extra repositories i get this:
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release:](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release:) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

following problems were found:
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-amd64_Packages)

4)i have installed Azureus through Automatix, but its not working when i start it asks me language to select and than if i am beginner, intermediate or expert, i select beginner thats it nothing happens after that. i have attached some screen shot about it.
5)Right at the end of any updates i get following error:
6)I manage to install a game star fighter which was as a deb package, but down know where it is or how to run it, can't reinstall cause it keeps telling me that there is a new version of star fighter on system. when i installed it, it mentioned some thing in user/share/games folder, but i can't find it.
7)when i was using windows i used DAP cause it gave me an option of right click and select all download all through DAP (this was for a page with 4 or 5 movie clips), but on Ubuntu i have to click one by one which is pain in the back side.
8)downloading torrent is another thing i used to do on windows but Ubuntu seems to do it really really slow (note i am using bittornado client)

i am really sorry if this post is long, i have tried every search i cannot to resolve these issues(almost 2 months) , now i gave up so i am doing this. i want to stay with Ubuntu, i don't want to back to windows.

---

### Post by SaturnTheIcy on 2006-08-07
1)To compile a programe you need all library ask the program.
For glob2-0.8.21 needs SDL_net.h library i don't know which library package you need, search on package manager to find SDL net or network, I thought.

2)This error "current build architecture amd64 does not appear in package's list (i386)" i think you have install amd64 edition check your package manager to find the program you need for amd64 edition.


3)You try to install dep, which allready instal on your system

For the other prob i dont know.

Sorry for my english it's little bad.

---

### Post by zorro26 on 2006-08-07
i cant find sdl_net.h under synaptic package manager, i have also tried sdl_net and sdl_network,
and when you say i need all llibrary is that for tar.bz2 and tar.gz packages, i have checked read me file and home page for the package, there no information on that??

---

### Post by zorro26 on 2006-08-08
Any one else, who can help me please??

---

### Post by sjbrun on 2006-08-08
Try searching synaptic for libsdl-net

---

### Post by zorro26 on 2006-08-09
thats already installed. can anyone please check my first post and advise me what should i do or what i am doing wrong..

---

### Post by SaturnTheIcy on 2006-08-09
try libsdl-net for developers. You need dev package for compile a program.

---

### Post by zorro26 on 2006-08-09
> **SaturnTheIcy said:**
> try libsdl-net for developers. You need dev package for compile a program.

yes thats installed aswell

---

### Post by SaturnTheIcy on 2006-08-10
Try this site they have deb package for ubuntu, if you want.
[http://globulation2.org/wiki/Download_and_Install](http://globulation2.org/wiki/Download_and_Install)

For the problem you have i don't know how to solve the prob.

And have the libs you want to compile.
Download them whit synaptic.

---

