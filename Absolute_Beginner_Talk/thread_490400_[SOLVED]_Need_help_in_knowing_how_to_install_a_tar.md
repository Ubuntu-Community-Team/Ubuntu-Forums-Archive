---
title: "[SOLVED] Need help in knowing how to install a tar.bz2 file."
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-07-02
Hello, I need your help.
I have tried a number of times to install a tar.bz2 (and other tar files) without success. Please see the enclosed attachment and look at the terminal commands I have typed and compare them to the instructions shown below the terminal for installing the tar.bz2 file. What am I doing wrong? Thank you for your assistance.

BTW, I "extracted" the tar.bz2 file into a folder named **gparted-0.3.3tar.gz**
kh

---

### Post by Seisen on 2007-07-02
if you extract it with archive manager you should end up with a folder called parted-1.8.7. From that directory you can run ./configure.

---

### Post by kittyhawk63 on 2007-07-02
> **Seisen said:**
> if you extract it with archive manager you should end up with a folder called parted-1.8.7. From that directory you can run ./configure.

Is archive manager a default program?

Edit: I found Archive Manager. I had never noticed it before. Thanks. I will give it a try.

---

### Post by Raineer on 2007-07-02
I'm a little confused by all the directory names :(  I just don't usually put extensions on mine

We need to see an 'ls' listing from the directory where you think you extracted it. If you still have a file with a .tar.gz extension then it's easy

```
tar -xf blablab.tar.gz
```

---

### Post by dreadlord_chris on 2007-07-02
you need to install the *build-essential* package:
```

sudo apt-get install build-essential

```
now that **./configure** should spit out **a whole lot more stuff**

---

### Post by kittyhawk63 on 2007-07-02
> **Raineer said:**
> I'm a little confused by all the directory names :(  I just don't usually put extensions on mine

We need to see an 'ls' listing from the directory where you think you extracted it. If you still have a file with a .tar.gz extension then it's easy

```
tar -xf blablab.tar.gz
```

The extension names were place there by the "Extract Here" command. I am now trying Archive Manager. I think that may have been my trouble all along.
kh

P.S. I gave the ls listing. See attachment. I am going to redo the extractions using Archive Manager.

---

### Post by kittyhawk63 on 2007-07-02
> **dreadlord_chris said:**
> you need to install the *build-essential* package:
```

sudo apt-get install build-essential

```now that **./configure** should spit out **a whole lot more stuff**

I've not done that. Thanks. I am going to install that right now.

Edit: Terminal shows it as already installed and up-to-date.
kh

---

### Post by Raineer on 2007-07-02
> P.S. I gave the ls listing. See attachment. I am going to redo the extractions using Archive Manager.
Well, you did...but you didn't give a 'ls' listing of the blabhlabh.tar.gz_FILES directory, unless I missed a second attachement.

As for the build-essentials, that is necessary in the end but won't fix your first bug because it didn't even *find* the configure file to start with.

---

### Post by kittyhawk63 on 2007-07-02
> **Raineer said:**
> Well, you did...but you didn't give a 'ls' listing of the blabhlabh.tar.gz_FILES directory, unless I missed a second attachement.

As for the build-essentials, that is necessary in the end but won't fix your first bug because it didn't even *find* the configure file to start with.

Let me work through the process of Archive Manager. The extension "FILES" does not show when using Archive Manager. I will repost if I cannot get ./configure to work after using Archive Manager. Thanks for all the help so far.
kh

---

### Post by Seisen on 2007-07-02
Worst case scenario you will be missing some dependencies.

---

### Post by kittyhawk63 on 2007-07-02
Edit: I think I forgot some lines in my attachment. I will repost in a few minutes. Sorry.
I'm back again,
I have tried to compile this [COLOR=Red]gparted-0.3.3tar.gz[/COLOR] file without success. I used the "Archive Manager" to extract the file. I hope that I have shown enough information below to let you see what I have done in "terminal." Do you know where I am making my mistake? I get along fine until I get to the "make" command. If you need more information, I will post it. Again, thanks for your assistance.
kh

[php]kittyhawk63@kittyhawk63:~$ cd Desktop
kittyhawk63@kittyhawk63:~/Desktop$ ls
ati-driver-installer-8.28.8.run  New Downloads
gparted-0.3.3tar.gz              parted-1.8.7.tar.bz2.png
kittyhawk63@kittyhawk63:~/Desktop$ cd gparted-0.3.3tar.gz
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz$ ls
atk-1.19.3           glibmm-2.12.1          gtkmm-2.8.12
atk-1.19.3.tar.bz2   glibmm-2.12.1.tar.bz2  gtkmm-2.8.12.tar.bz2
glib-2.13.5          gparted-0.3.3          parted-1.8.7
glib-2.13.5.tar.bz2  gparted-0.3.3.tar.gz   parted-1.8.7.tar.bz2
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz$ cd atk-1.19.3 
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz/atk-1.19.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for some Win32 platform... no
checking for native Win32 platform... no
checking for aclocal flags... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.5.7... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz/atk-1.19.3$ make
make: *** No targets specified and no makefile found.  Stop.
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz/atk-1.19.3$ ls
aclocal.m4             AUTHORS       configure.in  libtool        NEWS
atk                    ChangeLog     COPYING       ltmain.sh      po
atk.pc.in              config.guess  depcomp       MAINTAINERS    README
atk.spec               config.h.in   docs          Makefile.am    tests
atk.spec.in            config.log    gtk-doc.make  Makefile.in
atk-uninstalled.pc.in  config.sub    INSTALL       missing
atk-zip.sh.in          configure     install-sh    mkinstalldirs
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz/atk-1.19.3$ 

[/php]

---

### Post by Seisen on 2007-07-02
What errors are the make command giving you?

---

### Post by kittyhawk63 on 2007-07-02
I'm back again,
I have tried to compile this [COLOR=Red]gparted-0.3.3tar.gz[/COLOR] file without success. I used the "Archive Manager" to extract the file. I hope that I have shown enough information below to let you see what I have done in "terminal." Do you know where I am making my mistake? I get along fine until I get to the "make" command. If you need more information, I will post it. Again, thanks for your assistance.
kh

[php]kittyhawk63@kittyhawk63:~$ cd Desktop
kittyhawk63@kittyhawk63:~/Desktop$ ls
ati-driver-installer-8.28.8.run  New Downloads
gparted-0.3.3tar.gz              parted-1.8.7.tar.bz2.png
kittyhawk63@kittyhawk63:~/Desktop$ cd gparted-0.3.3tar.gz
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz$ ls
atk-1.19.3           glibmm-2.12.1          gtkmm-2.8.12
atk-1.19.3.tar.bz2   glibmm-2.12.1.tar.bz2  gtkmm-2.8.12.tar.bz2
glib-2.13.5          gparted-0.3.3          parted-1.8.7
glib-2.13.5.tar.bz2  gparted-0.3.3.tar.gz   parted-1.8.7.tar.bz2
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz$ cd atk-1.19.3
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz/atk-1.19.3$ ls
aclocal.m4             AUTHORS       configure.in  libtool        NEWS
atk                    ChangeLog     COPYING       ltmain.sh      po
atk.pc.in              config.guess  depcomp       MAINTAINERS    README
atk.spec               config.h.in   docs          Makefile.am    tests
atk.spec.in            config.log    gtk-doc.make  Makefile.in
atk-uninstalled.pc.in  config.sub    INSTALL       missing
atk-zip.sh.in          configure     install-sh    mkinstalldirs
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz/atk-1.19.3$ ./configure --without-readline
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for some Win32 platform... no
checking for native Win32 platform... no
checking for aclocal flags... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.5.7... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz/atk-1.19.3$ make
make: *** No targets specified and no makefile found.  Stop.
kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz/atk-1.19.3$[/php]I hope this answered the question to the last post.
kh


These lines are missing from above.
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for some Win32 platform... no
checking for native Win32 platform... no
checking for aclocal flags... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.5.7... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
[EMAIL="kittyhawk63@kittyhawk63:%7E/Desktop/gparted-0.3.3tar.gz"]kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz[/EMAIL]/atk-1.19.3$ make
make: *** No targets specified and no makefile found.  Stop.
[EMAIL="kittyhawk63@kittyhawk63:%7E/Desktop/gparted-0.3.3tar.gz"]kittyhawk63@kittyhawk63:~/Desktop/gparted-0.3.3tar.gz[/EMAIL]/atk-1.19.3$[/php]I hope this answered the question to the last post.
kh

---

### Post by Raineer on 2007-07-02
I know you already said that you think you missed some lines, however we only need about the last 10 lines from when you ran ./configure.  If you get to ANY point that will keep you from running "make", it will stop immediately.

All those "no's" you see in there aren't problems, if there was a problem it will stop and exit.

edit: Don't worry you're almost there ! ;p

---

### Post by Seisen on 2007-07-02
When you run ./configure it will spew the errors out at the end if there are any.

---

### Post by kittyhawk63 on 2007-07-02
> **Raineer said:**
> I know you already said that you think you missed some lines, however we only need about the last 10 lines from when you ran ./configure.  If you get to ANY point that will keep you from running "make", it will stop immediately.

All those "no's" you see in there aren't problems, if there was a problem it will stop and exit.

edit: Don't worry you're almost there ! ;p

I posted the last lines in my previous post. See at the end of the php. There must be a limit on how many line this feature takes. Sorry for the delay.
kh

---

### Post by Seisen on 2007-07-02
You need to install glib
```
sudo apt-get install libglib2.0-0 libglib2.0-dev
```

---

### Post by kittyhawk63 on 2007-07-02
Looks like I need to install GLIB. Is that correct?
kh

Edit: You beat me to it. Thanks. I will see how things go now.
kh

---

### Post by Raineer on 2007-07-02
Seisen beat me to it :( I had to look up the exact names, still too newb

---

### Post by Seisen on 2007-07-02
The easiest way to look up packages is to use the Ubuntu Package search engine in Firefox.

---

### Post by kittyhawk63 on 2007-07-02
I got it to work. I could not use "make install" until I used "sudo make install." Is that common?
kh

---

### Post by kittyhawk63 on 2007-07-02
> **Seisen said:**
> The easiest way to look up packages is to use the Ubuntu Package search engine in Firefox.

Explain further.
kh

---

### Post by Seisen on 2007-07-02
> **kittyhawk63 said:**
> I got it to work. I could not use "make install" until I used "sudo make install." Is that common?
kh

That is common every time I have done make install without sudo it does that.

On firefox you have a search engine  which should be on the right side  which has Google, Yahoo, etc...if you click the arrow and select Ubuntu Package search and type in the name of the packate it will either give you a keyword error or list the files in the Ubuntu repos that have that same package name or similar.

---

### Post by kittyhawk63 on 2007-07-02
> **Seisen said:**
> That is common every time I have done make install without sudo it does that.

On firefox you have a search engine  which should be on the right side  which has Google, Yahoo, etc...if you click the arrow and select Ubuntu Package search and type in the name of the packate it will either give you a keyword error or list the files in the Ubuntu repos that have that same package name or similar.

Thanks. I generally never use another search engine than Google. I will give this a try from now on when it comes to Ubuntu.
kh

---

### Post by Raineer on 2007-07-02
> **kittyhawk63 said:**
> I got it to work. I could not use "make install" until I used "sudo make install." Is that common?
kh

It's because configure and make are all done locally in that directory. make install physically installs it onto your system (and therefore needs root access to write outside of the /home/you/ directory)

---

### Post by mysticrider92 on 2007-07-02
Just as a suggestion, when installing packages on Ubuntu, I would not use the .tgz method unless absolutely necessary. Use apt, aptitude, or Synaptic to avoid problems. This method is much easier, and will save a lot of frustration when you need to install something else later.

---

### Post by kittyhawk63 on 2007-07-02
> **mysticrider92 said:**
> Just as a suggestion, when installing packages on Ubuntu, I would not use the .tgz method unless absolutely necessary. Use apt, aptitude, or Synaptic to avoid problems. This method is much easier, and will save a lot of frustration when you need to install something else later.

Good suggestion.
kh

---

