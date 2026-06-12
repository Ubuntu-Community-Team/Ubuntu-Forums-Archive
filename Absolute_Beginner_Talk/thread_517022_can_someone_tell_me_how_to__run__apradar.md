---
title: "can someone tell me how to  run  apradar?"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-08-04
i just installed apradar by converting a rpm to a deb with alien. I'm pretty sure it installed correctly. Now I want to run the progam.  How do I do that?  This us sine of the output from the terminal window:

brad@brad-laptop:~$ alien apradar-0.52-1.i586.rpm
Must run as root to convert to deb format (or you may use fakeroot).
brad@brad-laptop:~$ sudo alien apradar-0.52-1.i586.rpm
Password:
hostname: Unknown host
hostname: Unknown host
apradar_0.52-2_i386.deb generated
brad@brad-laptop:~$ dpkg -i apradar_0.52-2_i386.deb
dpkg: requested operation requires superuser privilege
brad@brad-laptop:~$ sudo dpkg -i apradar_0.52-2_i386.deb
Selecting previously deselected package apradar.
(Reading database ... 128308 files and directories currently installed.)
Unpacking apradar (from apradar_0.52-2_i386.deb) ...
Setting up apradar (0.52-2) ...
brad@brad-laptop:~$ gksu apradar
brad@brad-laptop:~$ ./apradar
bash: ./apradar: No such file or directory

brad@brad-laptop:~$ ls
amsn_received                 KNOWN-BUGS
apradar-0.52-1.i586.rpm       mnt
apradar_0.52-2_i386.deb       officedocs
automatix2.key                oralargument.odt
bluetooth                     parking.odt
CHANGES                       pictures
Desktop                       README
docs                          Shared
Examples                      smb4k
Firefox_wallpaper.png         splashimages
gtk-gnutella-downloads        tls1.50
Incomplete                    tls-1.5.0-linux-x86.tar.gz
install_flash_player_9_linux  wget-log
karpski-logfile.dat

---

### Post by asmoore82 on 2007-08-04
> **bradmayne said:**
> brad@brad-laptop:~$ alien apradar-0.52-1.i586.rpm
Must run as root to convert to deb format (or you may use fakeroot).

this error message puzzles me.
If a program told me that I could not convert a 'file' from one format to another in my own home folder
without granting said program root access, my response would not be suitable for public consumption.

:popcorn:

---

### Post by bradmayne on 2007-08-04
I got the info on how to "install" apradar from here on the ubuntu forums.  By the way their are other programs that need to be run as "root" i.e.- Wiirshehark.  So this brings me back ti the oriinal question how run "apradaf"?

---

### Post by Majorix on 2007-08-04
You can fakeroot instead of rooting.

```
sudo apt-get install fakeroot
```

then

```
fakeroot alien -d filename.rpm
```

install it

```
sudo dpkg -i packagename.deb
```

Then you can finally find where the package is located by typing this:

```
whereis packagename
```

---

### Post by diatribe on 2007-08-04
brad@brad-laptop:~$ gksu apradar
brad@brad-laptop:~$ ./apradar

when you typed gksu apradar and it didnt deliver an error message, I believe it started running.  try ps -x|grep apradar and see if it is just running in the background

---

### Post by bradmayne on 2007-08-08
ok so still no luck with using the "alien" command with apradar.  So i figured I would install from source.  I'm still having problems though.  After unpacking with the usual "tar -xvf" etc. I then used "./conigure".  I believe that went corectly.  Here is the output of the "./configure" command though:

root@brad-laptop:/home/brad/apradar-0.52# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
./configure: line 2147: src/Main.h: Permission denied
checking for /usr/include/gtkmm-2.0/gtkmm/window.h... yes
checking for /usr/include/iwlib.h... yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: executing depfiles commands
root@brad-laptop:/home/brad/apradar-0.52#

I then used the "make".  This is where I encountered problems  This is a copy of the output of the "make" command:

root@brad-laptop:/home/brad/apradar-0.52# make
Making all in src
make[1]: Entering directory `/home/brad/apradar-0.52/src'
if g++ -DPACKAGE_NAME=\"AP\ Radar\" -DPACKAGE_TARNAME=\"apradar\" -DPACKAGE_VERSION=\"0.52\" -DPACKAGE_STRING=\"AP\ Radar\ 0.52\" -DPACKAGE_BUGREPORT=\"donpdonp@users.sourceforge.net\" -DPACKAGE=\"apradar\" -DVERSION=\"0.52\" -I. -I.    `pkg-config --cflags gtkmm-2.0 `  -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cc; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
AccessPoint.h:60: error: extra qualification ‘AccessPoint::’ on member ‘operator==’
Main.h:18: error: extra qualification ‘Main::’ on member ‘ScanAPs’
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/brad/apradar-0.52/src'
make: *** [all-recursive] Error 1
root@brad-laptop:/home/brad/apradar-0.52#

can anyone explain to me the meaning of "Main.h:18: error: extra qualification ‘Main::’ on member ‘ScanAPs’"? By the way I have an atheros wireless card that supports monitor mode.  I am certain of this because I have used the monitor mode on many occasions.  So if anyone so if anyone can help I would really, really appreciate it!

---

### Post by bradmayne on 2007-08-09
no one has an answer?  I thought someone would be able to help me....

---

### Post by Chris S. on 2007-08-09
What was the problem with the .rpm package?  It didn't look like it kicked out any errors.  When you install packages, it doesn't necessarily drop the binary into your current directory, and probably not into your home directory either.  They'll show up somewhere like /usr/bin or /usr/share (or maybe other places, I don't fully know), and the binary will either be under an executable path, or will be symlinked to an executable path most of the time (there are occassions when this doesn't happen, which means you just have to find the binary on your machine yourself, which is easy enough).

Did you do what diatribe suggested and check ps -e for any running apradar processes?  It looked like there wasn't a problem with running gksu apradar, so it may actually be running without popping up a window.

Also, version 0.52 is supposed to have been released in May of 2004.  I have no idea what apradar is or what it's developers are or were up to, but it may be since unsupported, so try to stick with the .rpms or .debs if you can, maintain it yourself, or if all else fails, try a different application.  From the looks of it, it may be similar to wifi-radar, so you can try that if you can't get apradar working.  If it has what you need, that is.

---

### Post by bradmayne on 2007-08-14
i downloaded wifif radar and it seems pretty good for what i need to do.  I'm just lazy and don't feel like going to a terminal window to scan for networks.  So wifi radar works for me! thanks!!

---

### Post by mutsu on 2008-01-28
I found this thread while looking for an answer to the same problem. At that point I gave up looking on the web and started looking at the code.
I'm posting this in case someone else follows the same path I did and gets here :-)

4 changes in the code need to be made for it to function correctly. (At least in order to run and display available networks.
It appears the original author was following an older coding convention for c++.

In AccessPoint.h, on line 60,  remove AccessPoint::
In Main.h,  on line 18, remove Main::

Then errno is refered to and is no longer included implicity in one of the current includes and must be explicity included.

In AccessPoint.h, add line 15
include <errno.h>

Finally, scanning wasn't working correct. In a previous version it appears that either  struct iwreq was zero'd dynamically (Not sure how that would work) or memory management has changed a bit and zero'd the struct when declared. Clearing explicitly is now required.

ccode.cc line 34, add memset(&wrq, 0, sizeof(wrq));


That all it took to get it working on my laptop. Hope it helps the next person.

Mutsu.

---

