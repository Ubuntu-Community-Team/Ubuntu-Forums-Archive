---
title: "Problems installing eterm"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by MoRtYMer on 2006-04-16
Hi,
i'm new to ubuntu, installed on my laptop, all ok.

Now i want to install eterm but i'm having some problems:

When i tryed to install for the first time it couldn't find the package, then i alterered the source.list on /etc/apt/ and added this 2 lines:

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe 

then i've typed apt-get update and then apt-get install eterm and got this:

```

root@h0x:/etc/apt# apt-get install eterm
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  eterm: Depends: libast2 (>= 0.6-0pre2003010606) but it is not going to be installed
         Depends: libimlib2 but it is not installable
E: Broken packages
root@h0x:/etc/apt# 
```

I've got this error trying to install some other package.

What's this error, and why am i getting it?

Thx

---

### Post by MoRtYMer on 2006-04-16
Ok change the sources.list for one on the forum and the other error is no more, but now i have another error when doing apt-get update and dont know what it means:

```
Setting up locales (2.3.5-1ubuntu12.5.10.1) ...
Generating locales...
  en_US.UTF-8... done
  en_AU.UTF-8... donehange the sources.list for one on the forum, but now i have another error and dont know what it means:

  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8.../usr/share/i18n/locales/da_DK:195: LC_COLLATE: syntax error
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 locales
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone tell me why is doing that error?

Thx

---

### Post by MoRtYMer on 2006-04-16
Ok a restart solved it... this was dumb..](*,)

---

### Post by saax on 2006-06-03
I got problem installing Eterm too,i get this error

root@ubuntu:~/Eterm-0.9.3# ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

---

### Post by catlett on 2006-06-03
[QUOTE=saax]I got problem installing Eterm too,i get this error

root@ubuntu:~/Eterm-0.9.3# ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH[/QUOTE]

You need to install the application build essential it has the compilers gcc etc. Thats the error, the compilers aren't there to compile when you enter the ./configure command. So run this and then run the install again. ```
sudo apt-get install build-essential
```

---

### Post by saax on 2006-06-03
[QUOTE=catlett]You need to install the application build essential it has the compilers gcc etc. Thats the error, the compilers aren't there to compile when you enter the ./configure command. So run this and then run the install again. ```
sudo apt-get install build-essential
```[/QUOTE]


Now i get this 

root@ubuntu:~/Eterm-0.9.3# ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc -O ) works... yes
checking whether the C compiler (gcc -O ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking for strerror in -lcposix... no
checking for minix/config.h... no
checking for Cygwin environment... no
checking for mingw32 environment... no
checking host system type... powerpc-unknown-linux-gnu
checking build system type... powerpc-unknown-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking for object suffix... o
checking for executable suffix... no
checking command to parse /usr/bin/nm -B output... ok
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for distribution root... /root/Eterm-0.9.3
checking whether gcc needs -traditional... no
checking for a BSD compatible install... /usr/bin/install -c
checking host system type... powerpc-unknown-linux-gnu
checking whether build environment is sane... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking if malloc debugging is wanted... no
checking for sed... sed
checking for rm... rm
checking for cp... cp
checking for chmod... chmod
checking for tar... tar
checking for mkdir... mkdir
checking for ctags... true
checking for ar... ar
checking for mv... mv
checking for tic... tic
checking whether ln -s works... (cached) yes
checking for perl... /usr/bin/perl
checking for gawk... no
checking for mawk... mawk
checking for working const... yes
checking for inline... inline
checking whether byte ordering is bigendian... yes
checking for X... no
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for fcntl.h... yes
checking for termios.h... yes
checking for sys/ioctl.h... yes
checking for sys/select.h... yes
checking for sys/time.h... yes
checking for sys/sockio.h... no
checking for sys/byteorder.h... no
checking for malloc.h... yes
checking for utmpx.h... yes
checking for unistd.h... yes
checking for bsd/signal.h... no
checking for regex.h... yes
checking for regexp.h... yes
checking for stdarg.h... yes
checking for X11/Xmu/Atoms.h... no
checking for X11/Sunkeysym.h... no
checking whether time.h and sys/time.h may both be included... yes
checking for ANSI C header files... yes
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for uid_t in sys/types.h... yes
checking return type of signal handlers... void
checking for atexit... yes
checking for _exit... yes
checking for unsetenv... yes
checking for setutent... yes
checking for seteuid... yes
checking for memmove... yes
checking for putenv... yes
checking for strsep... yes
checking for setresuid... yes
checking for setresgid... yes
checking for memmem... yes
checking for usleep... yes
checking for snprintf... yes
checking for strcasestr... yes
checking for strcasechr... no
checking for strcasepbrk... no
checking for strrev... no
checking for nl_langinfo... yes
checking whether snprintf ignores n... no, snprintf is ok
checking for pow in -lm... yes
checking for library containing login... -lutil
checking for library containing logout... none required
checking for library containing getpwuid... none required
checking for debugging level... 4
checking for ptsname... yes
checking for grantpt... yes
checking for unlockpt... yes
checking for pty mechanism... SVR4
checking for pty group... tty
checking for saved uids... yes
checking if strict ICCCM compliance should be enabled... no
checking for XOpenDisplay in -lX11... no
ERROR:  You need libX11 to build Eterm.  Verify that you have libX11.a or
        libX11.so installed and that it is located in the X libraries
        directory shown above.  If it is in a different directory, try using
        the --x-libraries parameter to configure.
configure: error: Fatal:  libX11 not found.

---

### Post by catlett on 2006-06-03
This can happen when you build from source. All linux distributions are not built the same. So eterm may be geared towards (for example) red hat. They build the source around a library red hat has, libx11. When you run the compiling in ubuntu, ubuntu's linux install doesn't have that library. Then you start down the path of "dependency hell"
In linux things can't be installed without things being there already. Because in linux your not putting in new stuff all the time. You are replacing or building on other libraries/code etc. For instance if you start out with a. Someone makes b, a replacement for a. When it is installed the the system looks for a because it has a replacement for it, b. If a isn't there then b can't be installed because it is a replacement for a. It is not a stand alone thing made to be on its own, it is a replacement.
This is what is happening. Eterm is being built on libx11. Now you try to install libx11 and hope that is it.  Alot of times I'll install one library, it will get me further along but it will encounter another dependency I don't have.
All you can do is try and install the library it is looking for. Use aptitude instead of apt-get. It will work harder at dealing with dependencies. So try to install what it says is missing ```
sudo aptitude install libX11
``` and cross your fingers[-o<

---

### Post by saax on 2006-06-03
Ok,i saw i need libx11 and after that some other packages ,so i install everything i need and now  :confused: 

Eterm 0.9.3
Configuration:
--------------

  Source code location:       .
  Host System Type:           powerpc-unknown-linux-gnu
  Preprocessor:               gcc -I/usr/include
  Compiler:                   gcc -g -O2
  Linker:                     gcc -L/usr/lib  -lImlib2 -ldl -L/usr/lib   -last -lXext -lX11 -lutil -lm
  Install path:               /usr

  See src/feature.h for further configuration information.

  Now type 'make' to build Eterm 0.9.3.

ueulo@ubuntu:~/Eterm-0.9.3$ make
make  all-recursive
make[1]: Entering directory `/home/ueulo/Eterm-0.9.3'
Making all in src
make[2]: Entering directory `/home/ueulo/Eterm-0.9.3/src'
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..   -I/usr/include   -g -O2 -c actions.c
mkdir .libs
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include -g -O2 -c actions.c  -fPIC -DPIC -o .libs/actions.lo
In file included from feature.h:99,
                 from actions.c:27:
/usr/include/libast.h:78:28: error: X11/Intrinsic.h: No such file or directory
In file included from feature.h:99,
                 from actions.c:27:
/usr/include/libast.h:641: error: syntax error before 'Display'
/usr/include/libast.h:642: error: syntax error before 'Display'
/usr/include/libast.h:648: error: syntax error before 'libast_x_create_gc'
/usr/include/libast.h:648: error: syntax error before 'Display'
/usr/include/libast.h:649: error: syntax error before 'Display'
In file included from actions.c:32:
startup.h:122: error: syntax error before 'GC'
startup.h:122: warning: no semicolon at end of struct or union
startup.h:124: error: syntax error before '*' token
startup.h:124: warning: data definition has no type or storage class
startup.h:125: error: syntax error before 'fontset'
startup.h:125: warning: data definition has no type or storage class
startup.h:127: error: syntax error before '*' token
startup.h:127: warning: data definition has no type or storage class
startup.h:130: error: syntax error before '*' token
startup.h:130: warning: data definition has no type or storage class
startup.h:137: error: syntax error before '}' token
startup.h:137: warning: data definition has no type or storage class
startup.h:140: error: syntax error before 'TermWin'
startup.h:140: warning: data definition has no type or storage class
startup.h:142: error: syntax error before '*' token
startup.h:142: warning: data definition has no type or storage class
In file included from actions.h:30,
                 from actions.c:33:
events.h:60: error: syntax error before 'event_t'
events.h:60: warning: data definition has no type or storage class
events.h:61: error: syntax error before '*' token
events.h:62: error: syntax error before '*' token
events.h:92: error: syntax error before '*' token
events.h:98: error: syntax error before '*' token
events.h:99: error: syntax error before '*' token
events.h:100: error: syntax error before '*' token
events.h:101: error: syntax error before '*' token
events.h:102: error: syntax error before '*' token
events.h:103: error: syntax error before '*' token
events.h:104: error: syntax error before '*' token
events.h:105: error: syntax error before '*' token
events.h:106: error: syntax error before '*' token
events.h:107: error: syntax error before '*' token
events.h:108: error: syntax error before '*' token
events.h:109: error: syntax error before '*' token
events.h:110: error: syntax error before '*' token
events.h:111: error: syntax error before '*' token
events.h:112: error: syntax error before '*' token
events.h:113: error: syntax error before '*' token
events.h:114: error: syntax error before '*' token
events.h:115: error: syntax error before '*' token
events.h:116: error: syntax error before '*' token
events.h:117: error: syntax error before '*' token
events.h:118: error: syntax error before '*' token
events.h:119: error: syntax error before 'xerror_handler'
events.h:119: error: syntax error before '*' token
events.h:119: warning: data definition has no type or storage class
In file included from menus.h:29,
                 from actions.h:31,
                 from actions.c:33:
pixmap.h:193: error: syntax error before 'Pixel'
pixmap.h:193: warning: no semicolon at end of struct or union
pixmap.h:194: warning: data definition has no type or storage class
pixmap.h:198: error: syntax error before 'simage_t'
pixmap.h:198: warning: no semicolon at end of struct or union
pixmap.h:199: warning: data definition has no type or storage class
pixmap.h:203: error: syntax error before 'images'
pixmap.h:203: warning: data definition has no type or storage class
pixmap.h:228: error: syntax error before '*' token
pixmap.h:228: warning: data definition has no type or storage class
pixmap.h:229: error: syntax error before '*' token
pixmap.h:230: error: syntax error before '*' token
pixmap.h:231: error: syntax error before '*' token
pixmap.h:231: warning: data definition has no type or storage class
pixmap.h:232: error: syntax error before '*' token
pixmap.h:233: error: syntax error before '*' token
pixmap.h:237: error: syntax error before '*' token
pixmap.h:238: error: syntax error before '*' token
pixmap.h:239: error: syntax error before '*' token
pixmap.h:243: error: syntax error before '*' token
pixmap.h:246: error: syntax error before 'simage_t'
pixmap.h:252: error: syntax error before 'GC'
pixmap.h:258: error: syntax error before 'XWMHints'
In file included from actions.h:31,
                 from actions.c:33:
menus.h:62: error: syntax error before 'simage_t'
menus.h:62: warning: no semicolon at end of struct or union
menus.h:73: error: syntax error before '}' token
menus.h:73: warning: data definition has no type or storage class
menus.h:80: error: syntax error before 'GC'
menus.h:80: warning: no semicolon at end of struct or union
menus.h:82: error: syntax error before '*' token
menus.h:82: warning: data definition has no type or storage class
menus.h:84: error: syntax error before 'fontset'
menus.h:84: warning: data definition has no type or storage class
menus.h:88: error: syntax error before '*' token
menus.h:88: warning: data definition has no type or storage class
menus.h:89: error: syntax error before '}' token
menus.h:108: error: syntax error before '*' token
menus.h:109: error: syntax error before '*' token
menus.h:110: error: syntax error before '*' token
menus.h:111: error: syntax error before '*' token
menus.h:112: error: syntax error before '*' token
menus.h:113: error: syntax error before '*' token
menus.h:114: error: syntax error before '*' token
menus.h:115: error: syntax error before '*' token
menus.h:116: error: syntax error before '*' token
menus.h:123: error: syntax error before 'menuitem_t'
menus.h:127: error: syntax error before '*' token
menus.h:127: warning: data definition has no type or storage class
menus.h:128: error: syntax error before 'menuitem_t'
menus.h:129: error: syntax error before '*' token
menus.h:130: error: syntax error before '*' token
menus.h:130: warning: data definition has no type or storage class
menus.h:131: error: syntax error before '*' token
menus.h:132: error: syntax error before '*' token
menus.h:133: error: syntax error before '*' token
menus.h:134: error: syntax error before '*' token
menus.h:135: error: syntax error before '*' token
menus.h:143: error: syntax error before 'menuitem_t'
menus.h:147: error: syntax error before '*' token
In file included from actions.c:33:
actions.h:68: error: syntax error before '*' token
actions.h:89: error: syntax error before '*' token
actions.h:90: error: syntax error before '*' token
actions.h:91: error: syntax error before '*' token
actions.h:92: error: syntax error before '*' token
actions.h:97: error: syntax error before '*' token
In file included from actions.c:34:
command.h:334: error: syntax error before 'xim_input_context'
command.h:334: warning: data definition has no type or storage class
command.h:354: error: syntax error before 'create_fontset'
command.h:354: warning: data definition has no type or storage class
command.h:357: error: syntax error before '*' token
In file included from actions.c:40:
screen.h:236: error: conflicting types for 'screen'
startup.h:133: error: previous declaration of 'screen' was here
screen.h:304: error: syntax error before '*' token
screen.h:305: error: syntax error before '*' token
screen.h:306: error: syntax error before '*' token
In file included from actions.c:42:
scrollbar.h:129: error: syntax error before '*' token
scrollbar.h:130: error: syntax error before '*' token
scrollbar.h:131: error: syntax error before '*' token
scrollbar.h:132: error: syntax error before '*' token
scrollbar.h:133: error: syntax error before '*' token
scrollbar.h:134: error: syntax error before '*' token
scrollbar.h:135: error: syntax error before '*' token
scrollbar.h:136: error: syntax error before '*' token
scrollbar.h:137: error: syntax error before '*' token
scrollbar.h:138: error: syntax error before '*' token
In file included from actions.c:43:
term.h:164: error: syntax error before 'PixColors'
term.h:164: warning: data definition has no type or storage class
term.h:172: error: syntax error before '*' token
In file included from actions.c:44:
windows.h:34: error: syntax error before 'PixColors'
windows.h:34: warning: data definition has no type or storage class
windows.h:35: error: syntax error before 'Attributes'
windows.h:35: warning: data definition has no type or storage class
windows.h:36: error: syntax error before 'attr'
windows.h:36: warning: data definition has no type or storage class
windows.h:37: error: syntax error before 'szHint'
windows.h:37: warning: data definition has no type or storage class
windows.h:44: error: syntax error before 'get_bottom_shadow_color'
windows.h:44: error: syntax error before 'const'
windows.h:44: warning: data definition has no type or storage class
windows.h:45: error: syntax error before 'get_top_shadow_color'
windows.h:45: error: syntax error before 'const'
windows.h:45: warning: data definition has no type or storage class
windows.h:46: error: syntax error before 'get_color_by_name'
windows.h:46: warning: data definition has no type or storage class
windows.h:47: error: syntax error before 'get_color_by_pixel'
windows.h:47: warning: parameter names (without types) in function declaration
windows.h:47: warning: data definition has no type or storage class
actions.c:52: error: syntax error before '*' token
actions.c: In function 'action_handle_string':
actions.c:54: error: 'ev' undeclared (first use in this function)
actions.c:54: error: (Each undeclared identifier is reported only once
actions.c:54: error: for each function it appears in.)
actions.c:55: error: invalid type argument of '->'
actions.c:56: error: invalid type argument of '->'
actions.c:56: error: invalid type argument of '->'
actions.c: At top level:
actions.c:61: error: syntax error before '*' token
actions.c: In function 'action_handle_echo':
actions.c:63: error: 'ev' undeclared (first use in this function)
actions.c:64: error: invalid type argument of '->'
actions.c:66: error: request for member 'screen' in something not a structure or union
actions.c:66: error: request for member 'screen' in something not a structure or union
actions.c:69: error: request for member 'screen' in something not a structure or union
actions.c:69: error: invalid type argument of '->'
actions.c:73: error: invalid type argument of '->'
actions.c:73: error: invalid type argument of '->'
actions.c: At top level:
actions.c:78: error: syntax error before '*' token
actions.c: In function 'action_handle_script':
actions.c:80: error: 'ev' undeclared (first use in this function)
actions.c:81: error: invalid type argument of '->'
actions.c:82: error: invalid type argument of '->'
actions.c: At top level:
actions.c:87: error: syntax error before '*' token
actions.c: In function 'action_handle_menu':
actions.c:89: error: invalid type argument of '->'
actions.c:90: error: 'ev' undeclared (first use in this function)
actions.c:90: error: request for member 'parent' in something not a structure or union
actions.c:90: error: invalid type argument of '->'
actions.c: At top level:
actions.c:199: error: syntax error before '*' token
actions.c: In function 'action_dispatch':
actions.c:203: error: 'ev' undeclared (first use in this function)
actions.c:205: error: 'keysym' undeclared (first use in this function)
make[2]: *** [actions.lo] Error 1
make[2]: Leaving directory `/home/ueulo/Eterm-0.9.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ueulo/Eterm-0.9.3'
make: *** [all-recursive-am] Error 2

---

### Post by catlett on 2006-06-03
Welcome to hell:twisted: 
Only kidding but seriouisly it can drive you crazy. The only packages that are guaranteed to install and work are the ones in synaptic package manager. Next are .debs (debian packages) because ubuntu is based on debian sid (debians unstable version) so .debs usually install without a problem. Once you get to into compiling from source (extracting binaries from compressed tar files) you are rolling dice. Sometimes they install, sometimes they don't.
The only thing you can really do is start googling you errors are the name of the application and ubuntu. Hoipefully you will find a thread where someone has worked out the dependencies or managed a work around. Ubuntu's document storage area is full of little how tos and helpful hints. That is a good place to start a search.
You might want to start your own thread here and title it "dependency issues when installing eterm". Maybe someone who has it installed wil see it and give you the details. Sorry I can't be more help.

---

### Post by saax on 2006-06-03
Now,Im really confused ,after last install error i open Adept Manager and type Eterm and find it installed.But i didnt install it coz its version 0.9.2 I try to install 0.9.3 and when i look in AM for it to install it wasnt there.
Everything is ok now and its working ,but i still dont understand installation problems so many errors...

Thanks anyway catlett

---

### Post by catlett on 2006-06-03
Don't really know but always do a search in the package manager first (adept in kubuntu and synaptic in gnome, sorry about quoting synaptic earlier I run gnome and didn't realise you run kde)
That is the best install. But for your question. You can have a version installed and still compile from source without one knowing the other. When you compile it doesn't enter that repository/package manager world. So you can have a version in adept and be compiling one without knowing. Only if they are drawing from a third area in the filesystrem will it come up as an issue.
The crazy thing is you may have had eterm this whole time:-D 

P.S. Post any time you have an issue. I prefere this to bad television any day.

---

