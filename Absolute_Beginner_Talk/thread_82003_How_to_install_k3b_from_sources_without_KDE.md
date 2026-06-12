---
title: "How to install k3b from sources without KDE ?"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-25
./configure 
blocks asking for kde ..
  
Is there another way (than apt-get install k3b)
cos i would like to  be sure of havign all libraries and everythg install like perfect, last version and so on ...  cos hardware problems with k3b... 
Is there a way ??
thank you very much 

Best regards ,

Patrick

---

### Post by az on 2005-10-25
If you compile K3B from source, you will still need the kdelibs source to do that. 

If you want the latest k3b, download the source and get the -dev packages (kdelibs-dev...) and compile it yourself.  You will not be able to get around needing KDE.

---

### Post by clearnitesky on 2005-10-25
[QUOTE=azz]You will not be able to get around needing KDE[/QUOTE]

...because k3b is a KDE application.

Have you ever used XCDRoast? you may find that it does what you use k3b for. 
Alternatively, if you're feeling brave, you could try making CDs from the command line... commands such as cdrecord etc...

---

### Post by fannymites on 2005-10-25
GnomeBaker looks and works very much like k3b if that's any help - [http://gnomebaker.sourceforge.net/v2/](http://gnomebaker.sourceforge.net/v2/) I
t's in the breezy repos but I don't know about the hoary ones.
[EDIT] It's in the hoary universe repos.
A piccie - [http://gnomebaker.sourceforge.net/wp-content/gnomebaker1.png](http://gnomebaker.sourceforge.net/wp-content/gnomebaker1.png)

---

### Post by pbw on 2005-10-26
very lightweight and nice cd burning app is graveman. It holds as my choice for the lack of dependencies, speed and functionality.

Give it a shot, at worst it's only an apt-get remove away should you not like it. (it's in universe).

-- pbw

---

### Post by aysiu on 2005-10-26
[QUOTE=azz]If you compile K3B from source, you will still need the kdelibs source to do that. 

If you want the latest k3b, download the source and get the -dev packages (kdelibs-dev...) and compile it yourself.  You will not be able to get around needing KDE.[/QUOTE] Wait... this is just not true, if I'm understanding you correctly. I have Gnome and XFCE4 on my Ubuntu installation (no KDE), and I have K3B installed. I just did a ```
sudo apt-get install k3b
``` The necessary dependencies were resolved, and (again) I **do not** have KDE installed.

---

### Post by patrick295767 on 2005-10-26
[QUOTE=aysiu]Wait... this is just not true, if I'm understanding you correctly. I have Gnome and XFCE4 on my Ubuntu installation (no KDE), and I have K3B installed. I just did a ```
sudo apt-get install k3b
``` The necessary dependencies were resolved, and (again) I **do not** have KDE installed.[/QUOTE]

Which version of k3b do you have ? Is it the 0.12.5 version ?
I tried gnomebaker and nero linux but they dont burn Video DVD ... So, i thought that only K3B could let me burn this. 
  
I'll try then for my Video-DVD / Data-DVD burning : graveman and the xcdroast ...

Thank you again for your information !!!!!!!!!!

Best regards, 

Patrick

---

### Post by patrick295767 on 2005-10-26
[QUOTE=azz]If you compile K3B from source, you will still need the kdelibs source to do that. 

If you want the latest k3b, download the source and get the -dev packages (kdelibs-dev...) and compile it yourself.  You will not be able to get around needing KDE.[/QUOTE]

I'll try and let you know this evenign ... 
Thank you !!!!!!!!!!

Patrick

---

### Post by az on 2005-10-26
[QUOTE=aysiu]Wait... this is just not true, if I'm understanding you correctly. I have Gnome and XFCE4 on my Ubuntu installation (no KDE), and I have K3B installed. I just did a ```
sudo apt-get install k3b
``` The necessary dependencies were resolved, and (again) I **do not** have KDE installed.[/QUOTE]

You have kdelibs, kdebase kcontrol and libarts1 installed.  The binary package is split up into a number of different packages so that you can just keep what is neccessary.  This is not so if you compile kde from source.

So, installing k3b with apt pulls in the bare-minimum kde packages you need to run the app, but that was not the question.

dora@dora:~$ apt-cache show k3b
Package: k3b
Priority: optional
Section: otherosfs
Installed-Size: 4716
Maintainer: Jean-Michel Kelbert <kelbert@debian.org>
Architecture: i386
Version: 0.11.23-0ubuntu3
Depends: k3blibs (>= 0.11.23), kdelibs4 (>= 4:3.4.0), libart-2.0-2 (>= 2.3.16), libarts1 (>= 1.3.2), libasound2 (>> 1.0.8), libaudio2, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.2.ds1-4), libesd0 (>= 0.2.29-1) | libesd-alsa0 (>= 0.2.29-1), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgamin0, libgcc1 (>= 1:4.0-0pre6ubuntu4), libglib2.0-0 (>= 2.6.0), libice6 | xlibs (>> 4.1.0), libidn11 (>= 0.5.2), libogg0 (>= 1.1.2), libpng12-0 (>= 1.2.8rel), libqt3c102-mt (>= 3:3.3.3), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libvorbis0a (>= 1.0.1), libvorbisenc2 (>= 1.0.1), libvorbisfile3 (>= 1.0.1), libx11-6 | xlibs (>> 4.1.0), libxcursor1 (>> 1.1.2), libxext6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxinerama1, libxrandr2 | xlibs (>> 4.3.0), libxrender1, libxt6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1), cdrecord (>= 4:2.0+a18-1), cdparanoia (>= 3a9.8), mkisofs (>= 1.10), kdelibs-data (>= 4:3.3.99), kdebase-bin, kcontrol
Recommends: vcdimager (>= 0.7), dvd+rw-tools

---

### Post by patrick295767 on 2005-10-27
[QUOTE=azz]If you compile K3B from source, you will still need the kdelibs source to do that. 

If you want the latest k3b, download the source and get the -dev packages (kdelibs-dev...) and compile it yourself.  You will not be able to get around needing KDE.[/QUOTE]


I installed the kdelib4-dev_3.4.... from debian.org
then apt-get -f install
  
then ./configure   (from the folder k3b)
and i got this result:
./configure:
---------------
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
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
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
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
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... 
 
in the prefix, you've chose, are no KDE headers installed. This will fail. 
So, check this please and use another prefix!
--------------------------
  
Still not so easy ... I have only 2 months of experience with linux... Not yet enough as I can see ...
  
Thank you very much for ur knowledge support !!
  
With my best regards, 
  
Patrick

---

### Post by az on 2005-10-27
[QUOTE=patrick295767]I installed the kdelib4-dev_3.4.... from debian.org
then apt-get -f install
  
[/QUOTE]

What do you mean?  You installed that one file or you added a debian repository and apt-get installed it along with all the dependancies?

Because you are going to have to either backport all of kdebase or just switch to debian....

---

### Post by az on 2005-10-27
[http://k3b.plainblack.com/requirements](http://k3b.plainblack.com/requirements)

You can compile the latest k3b (0.12.5) with kde 3.2.  The version of kde in *Warty* is sufficient.

---

### Post by patrick295767 on 2005-10-28
[QUOTE=azz]What do you mean?  You installed that one file or you added a debian repository and apt-get installed it along with all the dependancies?

Because you are going to have to either backport all of kdebase or just switch to debian....[/QUOTE]
 
 
Since I not mastering that much the linux installing stuffs and terms, I'll try my best with my little experience in linux:
what I did was going to the [www.debian.org](www.debian.org)
i downloaded the file libs.4-dev...deb
  
then, xterm:
sudo dpkg -i libs.4-dev...deb
  
It said : please do stuff like apt-get -f install
  
then, it asked me whether i'd like to install additional stuffs required ...
  
then i said Yes, then it installed plenty other libs and stuffs ...
  
I did again sudo dpkg -i libs.4-dev...deb
to be sure 
  
then again apt-get -f install
then , nothing required else ... 
  
then, stuffs was installed i guess 
I am sorry: that's what can do Newbies ... withotu experience ...
  
I'll try to seek for Kde * warty * (size?) 
  
----
I also tried to install apt-get install k3b
thinking that i'll get extra libs but NO way
that doest help for compiling sources... 
    
--
Thank you for ur support !
and patience with a newbie !
  
Pat'

---

### Post by patrick295767 on 2005-10-28
By the way: that ' s my first post that became a draft - progression thread ... for a future how to wiki ... 

Thanks

pat'

---

### Post by patrick295767 on 2005-10-28
[QUOTE=patrick295767]By the way: that ' s my first post that became a draft - progression thread ... for a future how to wiki ... 

Thanks

pat'[/QUOTE]
   
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)
  
Regards,
 
Pat'

---

### Post by az on 2005-10-28
[QUOTE=patrick295767]Since I not mastering that much the linux installing stuffs and terms, I'll try my best with my little experience in linux:
what I did was going to the [www.debian.org](www.debian.org)
i downloaded the file libs.4-dev...deb
  
then, xterm:
sudo dpkg -i libs.4-dev...deb
  
It said : please do stuff like apt-get -f install
  
then, it asked me whether i'd like to install additional stuffs required ...
  
then i said Yes, then it installed plenty other libs and stuffs ...
  
I did again sudo dpkg -i libs.4-dev...deb
to be sure 
  
then again apt-get -f install
then , nothing required else ... 
  
then, stuffs was installed i guess 
I am sorry: that's what can do Newbies ... withotu experience ...
  
I'll try to seek for Kde * warty * (size?) 
  
----
I also tried to install apt-get install k3b
thinking that i'll get extra libs but NO way
that doest help for compiling sources... 
    
--
Thank you for ur support !
and patience with a newbie !
  
Pat'[/QUOTE]

Okay, I meant, do not install any packages from Debian.  They are in Ubuntu.  Even the ones from Warty are good enough.  I did not mean to say you should use those, just that you do not need to use debian packages.

You cannot mix repositories like that.

---

### Post by patrick295767 on 2005-10-28
[QUOTE=azz]Okay, I meant, do not install any packages from Debian.  They are in Ubuntu.  Even the ones from Warty are good enough.  I did not mean to say you should use those, just that you do not need to use debian packages.

You cannot mix repositories like that.[/QUOTE]
 
Thank you for this useful information !
Ubuntu is made on basis of Debian...
Will Ubuntu distri replace the Debian ?
I mean, choising an distribution is very important 'cos after some years, a distri can disappear ... and we won't find any updated-packages ... 
  
I'll try then ubuntu-packages!!

thanks again !!

patrick !

---

### Post by kaz_pinoy on 2006-07-11
Install konqueror 

sudo apt-get install konqueror

this should get all the KDE library to run K3b on Gnome

---

### Post by kaz_pinoy on 2006-07-11
install konqueror 

sudo apt-get install konqueror

this should get you all the KDE library to run K3B

then install k3b

---

