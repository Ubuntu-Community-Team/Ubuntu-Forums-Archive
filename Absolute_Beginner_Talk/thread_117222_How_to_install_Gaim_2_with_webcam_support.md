---
title: "How to install Gaim 2 with webcam support ??"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-14
How to install Gaim 2 with webcam support ??
  
Thank you very much ;,

Pat'

---

### Post by Turtle.net on 2006-01-14
It seems that Gaim 2 does not include gaim-vv (webcam support) for the moment.
Follow the news [http://gaim.sourceforge.net/]("http://gaim.sourceforge.net/")

---

### Post by patrick295767 on 2006-01-14
> The gaim-2.0.0beta1 can handle webcams in MSN. It's not entierly easy to get it working though.
You need gnutls, speex and some other things I don't know the name of.

When (if you decide to try it) compiling gaim 2.0.0-beta1, type ./configure --help to see available options and stuff (turn on everything you want, run ./configure and it'll tell you what you're missing, then google for the missing things and install them).

MSN users need to configure gaim with the option --enable-gnutls=yes to be able to log in. If you don't have this option MSN won't work.
  
I quote ... maybe v. difficult stilll

---

### Post by kakashi on 2006-01-14
if you want (and can wait ) i'll make a deb for you when i get back home (in 4 days). untill then try compiling it in with 
[URL="http://ubuntuforums.org/showthread.php?t=88014"]
try this guide i made.[/URL] please also post to bump it up.

./configure --prefix=$HOME/anydirectoryyouwant/ --(other options you want)

this will allow you to delete the installation if it screws up.

---

### Post by hen3rz on 2006-01-14
> if you want (and can wait ) i'll make a deb for you when i get back home (in 4 days). 
I would appreciate this as well!

---

### Post by Mission 10 on 2006-01-14
I'd be really interested in that also! IM with webcam support for MSN messanger is one of the only things that keeps XP on my system.. loads of my family around the US and UK use it to keep in touch. With it I am that much closer to ditching Microsoft!!

---

### Post by BLTicklemonster on 2006-01-15
Well, I'm stuck again. I've tried to install several things as of late, and they all run into the same problem. It seems that glib 2.0 is returned, but glib 2.* is actually what I have. (big freaking deal, just install dammit) It gives me some advise to uninstall or something, but I can't remember what exactly it says. 

This is really getting to be a pain in the ass when I try to install a new program and it refuses to install just because my machine can't remember that it has a newer version of something that it thinks it has. 

Is this something I could have corrected when installing something a while back but didn't have any idea what to do? 

I really like Ubuntu and linux, but running into these totally needless roadblocks is getting old.

---

### Post by dueY on 2006-01-15
The gaim page hasn't been updated for almost a month.  Any idea of when a stable build of gaim meant for public use will be released?

---

### Post by kakashi on 2006-01-15
[QUOTE=BLTicklemonster]Well, I'm stuck again. I've tried to install several things as of late, and they all run into the same problem. It seems that glib 2.0 is returned, but glib 2.* is actually what I have. (big freaking deal, just install dammit) It gives me some advise to uninstall or something, but I can't remember what exactly it says. 
[/quote]
watwere you doing.??? compiling from source. please post the exact output of the terminal. maybe otput it to a file and then paste or attach the file. output to file by 
```

command you eter >path/to/file

```
> 
This is really getting to be a pain in the ass when I try to install a new program and it refuses to install just because my machine can't remember that it has a newer version of something that it thinks it has. 

Is this something I could have corrected when installing something a while back but didn't have any idea what to do? 

I really like Ubuntu and linux, but running into these totally needless roadblocks is getting old.

welcome to linux. but don't think the roadblocks are not present in windows or anywhere else.

---

### Post by patrick295767 on 2006-01-15
[QUOTE=kakashi]if you want (and can wait ) i'll make a deb for you when i get back home (in 4 days). untill then try compiling it in with 
[URL="http://ubuntuforums.org/showthread.php?t=88014"]
try this guide i made.[/URL] please also post to bump it up.

./configure --prefix=$HOME/anydirectoryyouwant/ --(other options you want)

this will allow you to delete the installation if it screws up.[/QUOTE]
  
You would be an Angel for Us !!!
  
Btw, i am impressed by this making deb file by your own ... 
I hope I'll be better after years of using linux 

greetz

pat'

---

### Post by patrick295767 on 2006-01-15
[QUOTE=Mission 10]I'd be really interested in that also! IM with webcam support for MSN messanger is one of the only things that keeps XP on my system.. loads of my family around the US and UK use it to keep in touch. With it I am that much closer to ditching Microsoft!![/QUOTE]
  
Me, it's also same: impossible after 3-4 months now !
with that fu.... g      Logitech Messenger Webcam 
&& USB Logitech Microphone AK sthg... 
  
I love my Linux, and wish to make it one day, still 
  
I hope we wont return to XP, just for simple drivers for regular webcam for instance. 

:-(

Courage !

---

### Post by Sef on 2006-01-15
>  IM with webcam support for MSN messanger is one of the only things that keeps XP on my system.

While waiting for GAIM to get webcam support, have you tried amsn?  It does have webcam support.

---

### Post by patrick295767 on 2006-01-15
[QUOTE=Sef]While waiting for GAIM to get webcam support, have you tried amsn?  It does have webcam support.[/QUOTE]
  
I installed it frmo alvaro deb file, no prob with installing, but Impossible to accept the invitation to see the webcam of my dad ... 
I get such error msg ```
----------
Received Video Conference invitation from pierre - (Accept / Reject)
----------
----------
 Video Conference call canceled
----------
----------
Received Video Conference invitation from pierre - (Accept / Reject)
----------
----------
 Video Conference call accepted
----------
----------
 Initialization of the Audio/Video Plugin failed. Call Canceled
----------
----------
 Video Conference call canceled
----------
----------
 Video Conference call accepted
----------
----------
 Initialization of the Audio/Video Plugin failed. Call Canceled
----------
----------
 Video Conference call canceled
```
  
I am blocked.. 
I even removed my webcam logitech usb not working... 
every usb devices , and no results 
thinking that was a conflict ... 
 
 I am having no hopes now ... :-(
  
Greetz

---

### Post by Mission 10 on 2006-01-15
Horray for amsn! Works like a champ. Just an interesting sidenote... sudo brings up the older version of amsn which does not support webcams. If anyone is interested you should go to this address and download the deb file.

[http://amsn.sourceforge.net](http://amsn.sourceforge.net)

For new linux users: you must dpkg the deb file, if you are a extreme beginner like me and don't know how to do this then check out this link. It helped me out.

[http://www.newlinuxuser.com/howto-use-dpkg-to-install-deb-files/](http://www.newlinuxuser.com/howto-use-dpkg-to-install-deb-files/)

---

### Post by BLTicklemonster on 2006-01-16
[QUOTE=kakashi]watwere you doing.??? compiling from source. please post the exact output of the terminal. maybe otput it to a file and then paste or attach the file. output to file by 
```

command you eter >path/to/file

```


welcome to linux. but don't think the roadblocks are not present in windows or anywhere else.[/QUOTE]


Well, tar -xvzf gaim-2.0.0beta1.tar.gz goes fine, then I bill@ubuntu:~/gaim-2.0.0beta1$ ./configure and I get this:

```
bill@ubuntu:~/gaim-2.0.0beta1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking for a BSD-compatible install... /usr/bin/install -c
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking whether we are using the GNU C Library 2 or newer... yes
checking for ranlib... (cached) ranlib
checking for library containing strerror... none required
checking for an ANSI C-conforming const... yes
checking for signed... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for long long... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for stdint.h... (cached) yes
checking for SIZE_MAX... yes
checking for stdint.h... (cached) yes
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/sh: ./config.rpath: No such file or directory
done
checking for ptrdiff_t... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for asprintf... yes
checking for fwprintf... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for snprintf... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for wcslen... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... no
checking whether getc_unlocked is declared... yes
checking for iconv... yes
checking for iconv declaration...
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking for CFPreferencesCopyAppValue... (cached) no
checking for CFLocaleCopyCurrent... (cached) no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for locale.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for stdint.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for an ANSI C-conforming const... (cached) yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... (cached) yes
checking for strstr... yes
checking for atexit... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MEANWHILE... checking for HOWL... checking howl.h usability... no
checking howl.h presence... no
checking for howl.h... no
checking for sw_discovery_init in -lhowl... no
checking for SILC... checking for SILC... checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for uname... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.8.0, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at http://www.gtk.org/.
bill@ubuntu:~/gaim-2.0.0beta1$



```

lovely tidbit...

I have tried I think it's ldconfig after installing glib, but it says there's no ldconfig. And setting the environment variable PKG_CONFIG_PATH to point to the correct configuration files sounds like the thing to do, but I have no idea how one goes about doing such a wonderous thing...


*edit: okay, wtf is up with that? i686? I'm on i386...

---

### Post by dueY on 2006-01-16
[QUOTE=BLTicklemonster]

*edit: okay, wtf is up with that? i686? I'm on i386...[/QUOTE]

You probably are 686.  Aren't most computers 686 now, as in Pentium II+?  It's still compatible with 386 though.

---

### Post by BLTicklemonster on 2006-01-16
I guess I need to get out more... I thought 686 was 64 bit cpu...

---

### Post by BLTicklemonster on 2006-01-17
uname -r shows me using a 386

---

