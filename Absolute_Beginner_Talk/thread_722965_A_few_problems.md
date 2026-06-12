---
title: "A few problems"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Gusx1 on 2008-03-13
My problems are whenever i try to open gaim instant messenger it signs in then shows my buddy list then exits right after that, And my other problem is whenever i go into the terminal and it asks me  to do something involving my password i cannot type it in whats that mean?, also i am using Ubuntu 6.06 i think and i was wondering if its possible to upgrade say if i want beryl, And i have one question my firewall on windows for the last 2-3 years has been zone alarms.. I was wondering if there is a decent one for ubuntu firewall that is, Thanks

---

### Post by scragar on 2008-03-13
firstly, the terminal just doesn't show you typing, but still enter your password(enter to submit it), it's an extra security feature to stop people seeing how long your password is.

as for your gaim error open a terminal and type```
gaim
``` see what error message you get when it quits, post it here if it doesn't contain anything you don't want us to see(passwords or whatever)

---

### Post by Gusx1 on 2008-03-13
> **scragar said:**
> firstly, the terminal just doesn't show you typing, but still enter your password(enter to submit it), it's an extra security feature to stop people seeing how long your password is.

as for your gaim error open a terminal and type```
gaim
``` see what error message you get when it quits, post it here if it doesn't contain anything you don't want us to see(passwords or whatever)

wow thanks for the fast reply appreciate it! heres the thing from typing in gaim

gusx1@gusx1-desktop:~$ gaim
Gaim has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

It is possible that this bug is already fixed in CVS.
If you can reproduce the crash, please notify the gaim
maintainers by reporting a bug at
[http://gaim.sourceforge.net/bug.php](http://gaim.sourceforge.net/bug.php)

Please make sure to specify what you were doing at the time,
and post the backtrace from the core file. If you do not know
how to get the backtrace, please get instructions at
[http://gaim.sourceforge.net/gdb.php](http://gaim.sourceforge.net/gdb.php). If you need further
assistance, please IM either SeanEgn or LSchiere and
they can help you.
Aborted
gusx1@gusx1-desktop:~$

---

### Post by scragar on 2008-03-13
hmn... I'd say file a bug report about that, and upgrade to the latest version, but it's not gaim anymore(name changed to pidgin a while ago...).

[http://ubuntuforums.org/showthread.php?t=460324](http://ubuntuforums.org/showthread.php?t=460324) <-- guide on bulding pidgin from source here, but really it's proberly easier to do an upgrade or 2 from dapper(6.06) to something more up to date like fiesty(7.04) or the latest, gutsy(7.10)

ubuntu doesn't really need a firewall, since it keeps ports not in use closed, but firestarter is a nice choice.

---

### Post by kostkon on 2008-03-13
You could try to delete the configuration files for Gaim that you can find in the hidden folder named *.gaim*. To see hidden files/folders, open a nautilus window, and select *View -> Show Hidden Files*.

Try to delete at least the *prefs.xml* file. Take a backup of it first. If that does not solve your problem, then try to delete all of these XML configuration files.

Although, I cannot take any responsibility for any negative consequences of deleting these files, like losing your buddy list on the server side permanently.

Another good option would be to install *Pidgin*, the new name for *Gaim*. If you have 7.04 or newer, you can download a deb file for *Pidgin* from [*GetDeb*]("http://www.getdeb.net/").

---

### Post by Gusx1 on 2008-03-13
im on 6.06 im sure of it, i don't know how to update, also could someone provide a link to pidgen? please and thanks.

---

### Post by joshrobinson on 2008-03-13
this is source code, so you will have to compile it

[http://www.pidgin.im/download/source/]("http://www.pidgin.im/download/source/")

---

### Post by kostkon on 2008-03-13
> **Gusx1 said:**
> im on 6.06 im sure of it, i don't know how to update, also could someone provide a link to pidgen? please and thanks.

The site for *Pidgin* is [here]("http://www.pidgin.im/"). I think you will have to compile it yourself.

---

### Post by Oldsoldier2003 on 2008-03-13
> **joshrobinson said:**
> this is source code, so you will have to compile it

[http://www.pidgin.im/download/source/]("http://www.pidgin.im/download/source/")

a complete tutorial is here:
[http://ubuntuforums.org/showthread.php?t=613049](http://ubuntuforums.org/showthread.php?t=613049)

---

### Post by Gusx1 on 2008-03-13
alright i did everything in the tutorail so far but the make command doesn't work just says cannot find file, how can i install it from the directory on my desktop?

---

### Post by |{urse on 2008-03-13
Sounds like a pretty new user so ill save someone else the post

in order to compile that code you download the tar.gz and extract it to wherever
open a terminal and navigate your way to the directory where it is extracted to

so if you extracted it to a folder on your desktop it would be

cd /home/user/Desktop/placewhereyouextractedit

then type:
sudo su
enter your password
./configure
make
make install

close and re-open your terminal

then type "pidgin" without the quotes to run it

---

### Post by Gusx1 on 2008-03-13
> **|{urse said:**
> cd /home/user/Desktop/placewhereyouextractedit



i dont understand this part would it be cd /home/user/Desktop/pidgin-2.4.0 ?

---

### Post by |{urse on 2008-03-13
yes and replace /user with your username

---

### Post by joshrobinson on 2008-03-13
> **Gusx1 said:**
> i dont understand this part would it be cd /home/user/Desktop/pidgin-2.4.0 ?

well if you downloaded it to your desktop, then right clicked it and clicked extract here, then it would be on your desktop

so in a terminal type cd /home/your user name here/Desktop/pidgin-2.4.0

---

### Post by Gusx1 on 2008-03-13
alright now am i doing something wrong??

root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# make
make: *** No targets specified and no makefile found.  Stop.
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# make install
make: *** No rule to make target `install'.  Stop.
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0#

---

### Post by joshrobinson on 2008-03-13
na, see how you have an error there before you typed make? you have to take care of that problem before you can move on, try this command

```
 sudo apt-get install libxml2 libxml2-dev
```
then 
```
./configure
```
and see how it goes

---

### Post by |{urse on 2008-03-13
thats odd, the only reason you should get that error is if target "install" doen't exist, which it should..
did you type

make 

before you typed

make install
 
?

---

### Post by scragar on 2008-03-13
that would be a yes.
> root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# make
make: *** No targets specified and no makefile found. Stop.

---

### Post by Gusx1 on 2008-03-13
> **joshrobinson said:**
> na, see how you have an error there before you typed make? you have to take care of that problem before you can move on, try this command

```
 sudo apt-get install libxml2 libxml2-dev
```
then 
```
./configure
```
and see how it goes

tryed that same thing as above, no clue what im doing wrong :(

---

### Post by |{urse on 2008-03-13
derr /me slaps self. im goin to bed ^^

---

### Post by joshrobinson on 2008-03-13
> **|{urse said:**
> thats odd, the only reason you should get that error is if target "install" doen't exist, which it should..
did you type

make 

before you typed

make install
 
?

his config got an error, so there is no make file to make

---

### Post by joshrobinson on 2008-03-13
could you post your output again?
just the end 10-15 lines is all

---

### Post by |{urse on 2008-03-13
> **joshrobinson said:**
> his config got an error, so there is no make file to make
yeah i saw tht right after i posted =d :lolflag:

---

### Post by Gusx1 on 2008-03-13
> **joshrobinson said:**
> could you post your output again?
just the end 10-15 lines is all

i opened a new terminal to see if that was the problem here is the whole thing.

gusx1@gusx1-desktop:~$ cd /home/gusx1/Desktop/pidgin-2.4.0
gusx1@gusx1-desktop:~/Desktop/pidgin-2.4.0$ sudo su
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# make
make: *** No targets specified and no makefile found.  Stop.
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# makeinstall
bash: makeinstall: command not found
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0#

---

### Post by |{urse on 2008-03-13
try,
sudo apt-get install libxml-parser-perl

---

### Post by Gusx1 on 2008-03-13
> **|{urse said:**
> try,
sudo apt-get install libxml-parser-perl

alright what next, and thanks for your continued help guys/girls.

root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# sudo apt-get install libxml-parser-perl
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl liburi-perl libwww-perl
Suggested packages:
  libio-socket-ssl-perl
Recommended packages:
  libmailtools-perl libhtml-format-perl libcompress-zlib-perl
The following NEW packages will be installed:
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl liburi-perl libwww-perl libxml-parser-perl
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1064kB of archives.
After unpacking, 3043kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main libhtml-tagset-perl 3.10-1 [13.6kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main libhtml-parser-perl 3.48-1 [103kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main liburi-perl 1.35-1 [87.8kB]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main libwww-perl 5.803-4 [358kB]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main libhtml-tree-perl 3.19.01-1 [208kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main libxml-parser-perl 2.34-4 [292kB]
Fetched 1064kB in 1s (605kB/s)
Selecting previously deselected package libhtml-tagset-perl.
(Reading database ... 74664 files and directories currently installed.)
Unpacking libhtml-tagset-perl (from .../libhtml-tagset-perl_3.10-1_all.deb) ...
Selecting previously deselected package libhtml-parser-perl.
Unpacking libhtml-parser-perl (from .../libhtml-parser-perl_3.48-1_i386.deb) ...
Selecting previously deselected package liburi-perl.
Unpacking liburi-perl (from .../liburi-perl_1.35-1_all.deb) ...
Selecting previously deselected package libwww-perl.
Unpacking libwww-perl (from .../libwww-perl_5.803-4_all.deb) ...
Selecting previously deselected package libhtml-tree-perl.
Unpacking libhtml-tree-perl (from .../libhtml-tree-perl_3.19.01-1_all.deb) ...
Selecting previously deselected package libxml-parser-perl.
Unpacking libxml-parser-perl (from .../libxml-parser-perl_2.34-4_i386.deb) ...
Setting up libhtml-tagset-perl (3.10-1) ...
Setting up libhtml-parser-perl (3.48-1) ...
Setting up liburi-perl (1.35-1) ...
Setting up libwww-perl (5.803-4) ...
Setting up libxml-parser-perl (2.34-4) ...
Setting up libhtml-tree-perl (3.19.01-1) ...
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0#

---

### Post by joshrobinson on 2008-03-13
```

sudo apt-get install libxml-parser-perl
```

then do your ./configure again

EDIT: man we all posted the same thing at the same time

---

### Post by |{urse on 2008-03-13
now try compiling it

---

### Post by Gusx1 on 2008-03-13
seems to still not be working? i wonder why not? is there another program i can use for msn?

root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# sudo apt-get install libxml-parser-perl
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl liburi-perl libwww-perl
Suggested packages:
  libio-socket-ssl-perl
Recommended packages:
  libmailtools-perl libhtml-format-perl libcompress-zlib-perl
The following NEW packages will be installed:
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl liburi-perl libwww-perl libxml-parser-perl
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1064kB of archives.
After unpacking, 3043kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main libhtml-tagset-perl 3.10-1 [13.6kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main libhtml-parser-perl 3.48-1 [103kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main liburi-perl 1.35-1 [87.8kB]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main libwww-perl 5.803-4 [358kB]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main libhtml-tree-perl 3.19.01-1 [208kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main libxml-parser-perl 2.34-4 [292kB]
Fetched 1064kB in 1s (605kB/s)
Selecting previously deselected package libhtml-tagset-perl.
(Reading database ... 74664 files and directories currently installed.)
Unpacking libhtml-tagset-perl (from .../libhtml-tagset-perl_3.10-1_all.deb) ...
Selecting previously deselected package libhtml-parser-perl.
Unpacking libhtml-parser-perl (from .../libhtml-parser-perl_3.48-1_i386.deb) ...
Selecting previously deselected package liburi-perl.
Unpacking liburi-perl (from .../liburi-perl_1.35-1_all.deb) ...
Selecting previously deselected package libwww-perl.
Unpacking libwww-perl (from .../libwww-perl_5.803-4_all.deb) ...
Selecting previously deselected package libhtml-tree-perl.
Unpacking libhtml-tree-perl (from .../libhtml-tree-perl_3.19.01-1_all.deb) ...
Selecting previously deselected package libxml-parser-perl.
Unpacking libxml-parser-perl (from .../libxml-parser-perl_2.34-4_i386.deb) ...
Setting up libhtml-tagset-perl (3.10-1) ...
Setting up libhtml-parser-perl (3.48-1) ...
Setting up liburi-perl (1.35-1) ...
Setting up libwww-perl (5.803-4) ...
Setting up libxml-parser-perl (2.34-4) ...
Setting up libhtml-tree-perl (3.19.01-1) ...
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  af am ar az be@latin bg bn bs ca ca@valencia cs da de dz el en_AU en_CA en_GB eo es et eu fa fi fr gl gu he hi hu id it ja ka kn ko ku lo lt mk my_MM nb ne nl nn pa pl pt_BR pt ps ro ru si sk sl sq sr sr@latin sv ta te th tr uk ur vi xh zh_CN zh_HK zh_TW
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
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
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for time_t... yes
checking size of time_t... 4
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... yes
checking for strstr... yes
checking for atexit... yes
checking for setlocale... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for fileno()... yes
checking for the %z format string in strftime()... yes
checking for GLIB... no
no
configure: error:

You must have the GLib 2.0 development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.

root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# make
make: *** No targets specified and no makefile found.  Stop.
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0#

---

### Post by |{urse on 2008-03-13
rofl

---

### Post by |{urse on 2008-03-13
sudo apt-get install libglib2.0-dev

---

### Post by Gusx1 on 2008-03-13
> **|{urse said:**
> sudo apt-get install libglib2.0-dev

now theres one more thing left at the bottom

root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# sudo apt-get install libglib2.0-dev
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  libglib2.0-doc
The following NEW packages will be installed:
  libglib2.0-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 498kB of archives.
After unpacking, 1995kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main libglib2.0-dev 2.10.3-0ubuntu1 [498kB]
Fetched 498kB in 1s (466kB/s)
Selecting previously deselected package libglib2.0-dev.
(Reading database ... 74977 files and directories currently installed.)
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.10.3-0ubuntu1_i386.deb) ...
Setting up libglib2.0-dev (2.10.3-0ubuntu1) ...
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  af am ar az be@latin bg bn bs ca ca@valencia cs da de dz el en_AU en_CA en_GB eo es et eu fa fi fr gl gu he hi hu id it ja ka kn ko ku lo lt mk my_MM nb ne nl nn pa pl pt_BR pt ps ro ru si sk sl sq sr sr@latin sv ta te th tr uk ur vi xh zh_CN zh_HK zh_TW
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
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
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for time_t... yes
checking size of time_t... 4
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... yes
checking for strstr... yes
checking for atexit... yes
checking for setlocale... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for fileno()... yes
checking for the %z format string in strftime()... yes
checking for GLIB... yes
checking for X... no
checking for GTK... no
no
configure: error:

You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you want to build only Finch then specify --disable-gtkui when running configure.

root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0# make
make: *** No targets specified and no makefile found.  Stop.
root@gusx1-desktop:/home/gusx1/Desktop/pidgin-2.4.0#

---

### Post by joshrobinson on 2008-03-13
have you ever installed this?

```
sudo apt-get install build-essential
```

---

### Post by |{urse on 2008-03-13
if you follow the steps on this page to upgrade to feisty
[https://help.ubuntu.com/community/FeistyUpgrades]("https://help.ubuntu.com/community/FeistyUpgrades")
installing programs will be much much easier as your dependencies will be more up to date.

---

### Post by Gusx1 on 2008-03-13
> **joshrobinson said:**
> have you ever installed this?

```
sudo apt-get install build-essential
```

yes i have it seems

---

### Post by joshrobinson on 2008-03-13
```
sudo apt-get install libgtk2.0-0 libgtk2.0-dev
```

and try to configure again

---

### Post by Gusx1 on 2008-03-13
> **joshrobinson said:**
> ```
sudo apt-get install libgtk2.0-0 libgtk2.0-dev
```

and try to configure again

FIANLLY its making it now theres way to much to copy, once its done making i do "make install" as |{urse said correct? btw thanks to everyone who helped if it works when im finally done

---

### Post by |{urse on 2008-03-13
yes
make install
su gusx1
pidgin

---

### Post by joshrobinson on 2008-03-13
> **Gusx1 said:**
> FIANLLY its making it now theres way to much to copy, once its done making i do "make install" as |{urse said correct? btw thanks to everyone who helped if it works when im finally done

yeah just make sure you

```
sudo make install
```

because installing requires root permissions.. but it seems you are logged in as root, so make install should do fine

---

### Post by Gusx1 on 2008-03-13
alright seems its installed now how do i make it so its listed under internet??, also one last thanks to everyone who helped appreciate it :)

and i got one error

gusx1@gusx1-desktop:~$ pidgin

(pidgin:27474): Pango-WARNING **: Error loading GPOS table 4097

---

### Post by |{urse on 2008-03-13
ur quite welcome ^^

---

### Post by Gusx1 on 2008-03-13
is anyone able to help with my last error? please and thanks :)

---

### Post by joshrobinson on 2008-03-13
> **Gusx1 said:**
> alright seems its installed now how do i make it so its listed under internet??, also one last thanks to everyone who helped appreciate it :)

and i got one error

gusx1@gusx1-desktop:~$ pidgin

(pidgin:27474): Pango-WARNING **: Error loading GPOS table 4097

right click your applications menu in the top left, click "Edit menu's" click internet then click new item, name Pidgin and command Pidgin pick an icon, if you can find the pidgin one in there somewhere, or any icon you like

---

### Post by |{urse on 2008-03-13
what exactly do you mean by "listed under the internet"? your friends should be able to see you when you log into your respective aol, msn, etc. accounts.:confused:

---

### Post by |{urse on 2008-03-13
ah ^_- gotcha, u mean in the menu

---

### Post by Gusx1 on 2008-03-13
> **|{urse said:**
> what exactly do you mean by "listed under the internet"? your friends should be able to see you when you log into your respective aol, msn, etc. accounts.:confused:

i ment in the application area, and i still cannot actually log in because it will open up the log displaying my email witch i added, but then i get this error witch probally means that the main menu to log in wont pop up.

gusx1@gusx1-desktop:~$ pidgin

(pidgin:27579): Pango-WARNING **: Error loading GPOS table 4097

---

### Post by joshrobinson on 2008-03-13
for your error, open your home folder, go to view hidden files, then delete .purple
empty your trash, and try to start pidgin again

---

### Post by |{urse on 2008-03-13
wow i dont know..
should he try 
sudo apt-get install reinstall pango?
(don't do this yet gusx1)

---

### Post by Gusx1 on 2008-03-13
> **joshrobinson said:**
> for your error, open your home folder, go to view hidden files, then delete .purple
empty your trash, and try to start pidgin again

i just deleted .purple witch was a file folder and cleared my trash bin but its still the same error.

---

### Post by joshrobinson on 2008-03-13
> **Gusx1 said:**
> i just deleted .purple witch was a file folder and cleared my trash bin but its still the same error.

are you running pidgin as your user, or as root in a terminal?
run it as a normal user if you havent yet

---

### Post by Gusx1 on 2008-03-13
> **joshrobinson said:**
> are you running pidgin as your user, or as root in a terminal?
run it as a normal user if you havent yet

i tried both terminal and normal user, it seems that pidgin DOES open and puts itself in the tray and shows msn as "SSL support is needed for msn please install a supported SSL libary"

---

### Post by |{urse on 2008-03-13
sudo apt-get install libnss-dev libnspr-dev

from what im reading you may have to 

./configure
make
sudo make install

all over again if that doesnt work

---

### Post by joshrobinson on 2008-03-13
```
sudo apt-get install libnss3-0d libnss3-dev libnspr4-0d libnspr4-dev
```

if it doesnt work after installing these, you will probably have to re compile pidgin
so do your

./configure

make

make install

over again, but the hard stuff is done, you just have to wait for it to finish

---

### Post by |{urse on 2008-03-13
you should really consider backing up all of your data and upgrade to the latest version of ubuntu.

---

### Post by Gusx1 on 2008-03-13
> **|{urse said:**
> you should really consider backing up all of your data and upgrade to the latest version of ubuntu.

yeah im gonna do so now. Thanks guys, appreciate it

---

### Post by |{urse on 2008-03-13
hey, not a problem! Let us know if you have any more "a few problems" :lolflag:

---

