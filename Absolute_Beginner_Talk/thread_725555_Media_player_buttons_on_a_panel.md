---
title: "Media player buttons on a panel??"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-15
How do I get media buttons, like play/pause back and forward, on a panel which controls Amarok? 

Thanks,
Tom

---

### Post by talsemgeest on 2008-03-15
Have you seen someone who does it?

---

### Post by Tom--d on 2008-03-15
Yes. In the past I've seen screen shorts with the buttons on them..

Its like when you minmize windows media player and a mini little player is placed in the task bar.

---

### Post by talsemgeest on 2008-03-15
Sorry, I can't find anything either...

---

### Post by hyperair on 2008-03-15
Simple enough, just create a series of launchers on your panel.

For play/pause, the command is: dcop amarok player playPause
For next, the command is: dcop amarok player next
for prev, the command is : dcop amarok player prev

Position those three launchers next to each other, give them suitable icons, and titles, and you should be good to go.

---

### Post by Tom--d on 2008-03-16
Ah thank you!

---

### Post by hyperair on 2008-03-16
It should be noted that this will only work until Amarok 2 is released. Amarok 2 uses DBUS, whereas Amarok uses DCOP.

---

### Post by Tom--d on 2008-03-16
There is a amarok 2?

---

### Post by Ub1476 on 2008-03-16
Amarok 2 is in pre-alpha. In other words, do not use it.

Install the "music applet" from Synaptic, and set it to use Amarok (in plugins).

---

### Post by jayson.rowe on 2008-03-16
Are you using GNOME? If so, you might want to try music-applet (apt-get install music-applet) that may be what you've seen - after install just right-click on the panel and add the music-applet.

---

### Post by hyperair on 2008-03-16
Does music-applet work with Amarok? The last time I tried using it, there wasn't Amarok support.

---

### Post by Ub1476 on 2008-03-16
Well, I can confirm that version 2.3.0 works with it.

---

### Post by Tom--d on 2008-03-16
> **jayson.rowe said:**
> Are you using GNOME? If so, you might want to try music-applet (apt-get install music-applet) that may be what you've seen - after install just right-click on the panel and add the music-applet.

It doesn't support Amarok

---

### Post by Ub1476 on 2008-03-16
**How to get Amarok support for music-applet**

First, remove music-applet if it's installed.

Download version 2.3.0 from [here]("http://www.kuliniewicz.org/music-applet/downloads/").

Extract the archieve and cd into it. 

```
cd nameofmusicappletfolder
```

Install it with:

```
./configure
make
sudo make install
```

Apply to panel. Logout and login might be necessary.

---

### Post by Tom--d on 2008-03-16
I get this:

```

tom@Laptop:~/Desktop/music-applet-2.3.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking the maximum length of command line arguments... 98304
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether to enable strict checks... (cached) no
checking whether to enable deprecated APIs... (cached) yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers
tom@Laptop:~/Desktop/music-applet-2.3.0$ make
make: *** No targets specified and no makefile found. Stop.
tom@Laptop:~/Desktop/music-applet-2.3.0$ 
```

---

### Post by Ub1476 on 2008-03-16
**configure: error: could not find Python headers**

Search for python headers in Synaptic and install it. Then run ./configure again.

---

### Post by Tom--d on 2008-03-16
which one do I install? There are so many. And none of them are called Python Headers

---

### Post by Ub1476 on 2008-03-16
I'm not sure, sorry. But make sure [those]("http://packages.ubuntu.com/source/gutsy/gnome/music-applet") are installed at least.

---

### Post by hyperair on 2008-03-16
I think my method works much better =D At least there's no compilation involved. Until the next version of music-applet which has Amarok supprot gets debs that is.

EDIT: By the way, to get the required headers for you to compile:
```
sudo apt-get build-dep music-applet
```

Then just compile normally. It should work fine this time.

---

### Post by Tom--d on 2008-03-16
```
tom@Laptop:~$ sudo apt-get build-dep music-applet
[sudo] password for tom:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some &#8216;source&#8217; URIs in your sources.list
tom@Laptop:~$ 

```

---

### Post by lswest on 2008-03-16
that means you have to go to system-->administration-->software sources, and check the boxes on the main page, and in the third-party tab, where they refer to "sources"

---

### Post by npfiii on 2008-03-16
Hi,

Following the instructions so far, I've managed to install Music Applet, but when I try to configure it for Amarok, it tells me there is "*No module named kdecore*"

Any help gratefully received.

---

### Post by KhaaL on 2008-04-17
> **npfiii said:**
> Hi,

Following the instructions so far, I've managed to install Music Applet, but when I try to configure it for Amarok, it tells me there is "*No module named kdecore*"

Any help gratefully received.

I also have this issue and have no idea how to fix it.

---

### Post by hyperair on 2008-04-17
Install the "python-kde3" package. Apparently that package is missing from the dependencies.

---

### Post by KhaaL on 2008-04-17
> **hyperair said:**
> Install the "python-kde3" package. Apparently that package is missing from the dependencies.

Thanks, but now i get "No module named pcop" :-|

---

### Post by FunkWarrior on 2008-05-08
try

```
sudo apt-get install python-dcop 
```

---

