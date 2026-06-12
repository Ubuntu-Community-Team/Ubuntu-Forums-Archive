---
title: "Having some problems, please help!!"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by sec9456782 on 2007-08-10
Just download ubuntu today, so yeah i'm a complete noob. I have to say, its a great OS.
Anyway, i download a program called msn shadow in deb format and installed it. I can't seem to find the executable for it anywhere and so i have no idea how to run the program. I think i may have found it but am not sure. It was in usr/local/bin.
There is a file a 286kb file in there with an icon but no extension and im assuming this is the program. When i click it nothing happens so i tried opening it from the terminal and i got the following error: 
ubuntu@ubuntu:/usr/local/bin$ msnshadow
msnshadow: error while loading shared libraries: libkdeui.so.4: cannot open shared object file: No such file or directory
ubuntu@ubuntu:/usr/local/bin$ 

I'm completely lost, anybody got any advice?
THanks

---

### Post by misfitpierce on 2007-08-10
The website says this:

This software depends on QT and libmimic (farsight.sourceforge.net)

Did you perhaps check that other website for needed objects?

---

### Post by sec9456782 on 2007-08-10
THanks! SO i should install farsight?

---

### Post by misfitpierce on 2007-08-10
I'm guessing it might contain the packages you need. Or maybe try QT and libmimic seperate through package manager. Or search online. As I have not used im not 100% sure. The website does point you to there though so why not try it.

---

### Post by sec9456782 on 2007-08-10
I went to download farsight and then i extract the folder from the .gz file. I tried compiling using a guide, but i get the following error. I'm completely lost;
ubuntu@ubuntu:~/Desktop/farsight-0.1.3.1$ ./configure
configure: configuring farsight for development with nano 1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
ubuntu@ubuntu:~/Desktop/farsight-0.1.3.1$ 
Stop.

ALso, when i try to open "config.log" i get an error saying there is no config log

---

### Post by hyper_ch on 2007-08-10
shouldn't the .deb file also have resolved the dependencies?

---

### Post by sec9456782 on 2007-08-10
UNfortunately, i couln't seem to find the deb version on: [http://farsight.freedesktop.org/wiki/](http://farsight.freedesktop.org/wiki/)
In the archive there were only .gz versions

---

### Post by misfitpierce on 2007-08-10
I believe he meant for first package... and I would have thought so but the package from site specifically asks you to have those 2 things listed and points to that site with other program. Honestly I don't use MSN or this program so I have no idea. If your compiling from tar.gz and building though do you have build-essential installed?

sudo apt-get install build-essential

---

### Post by sec9456782 on 2007-08-10
THanks, i just installed the build essential and i didn't get that error this time. Now i got another problem though, any idea what this means:
checking for GLIB... configure: error: This package requires GLib >= 2.6.0 to compile

---

### Post by misfitpierce on 2007-08-10
Only package I could think of that I know which may work is this...

sudo apt-get install libglib2.0-dev

Devel packages for Glib used for building etc.

But what it means is you need newer Glib for building so either you need Glib or Glib and glib-dev for building packages which require it. Not 100%

---

### Post by sec9456782 on 2007-08-10
THanks fixed that problem now i got another one (lol): 
checking for GST... configure: error: This package requires GStreamer to compile

Nvm, problem solved. THanks so much for the help.\



3 new prblems :/
It seems i have another problem, when i do "make install" after ./configure and "make" i get the following error:
/usr/bin/install: cannot create regular file `/usr/local/lib/libfarsight-0.1.so.0.0.0': Permission denied
make[3]: *** [install-libLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/ubuntu/Desktop/farsight-0.1.3.1/farsight'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/ubuntu/Desktop/farsight-0.1.3.1/farsight'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/ubuntu/Desktop/farsight-0.1.3.1/farsight'
make: *** [install-recursive] Error 1






LOl another problem, i get up to the "make check" stage after the "make" stage and i get the following error: 
make  check-TESTS
make[2]: Entering directory `/home/ubuntu/Desktop/farsight-0.1.3.1/tests'
** Message: looking for plugins in /usr/local/lib/farsight-0.1/
Plugin not found or without init_function
Plugin not supported

** ERROR **: RTP plugin not found
aborting...
/bin/bash: line 4: 20504 Aborted                 (core dumped) ${dir}$tst
FAIL: farsight_test_rtp
** Message: looking for plugins in /usr/local/lib/farsight-0.1/
Plugin not found or without init_function
Plugin not supported

** ERROR **: RTP plugin not found
aborting...
/bin/bash: line 4: 20532 Aborted                 (core dumped) ${dir}$tst
FAIL: farsight_test_rtp_2
usage : test remoteip remoteport
FAIL: farsight_test_rtp_3
usage : test remoteip remoteport
FAIL: farsight_test_rtp_3_v
usage : test remoteip remoteport
FAIL: farsight_test_rtp_4
** Message: looking for plugins in /usr/local/lib/farsight-0.1/
Plugin not found or without init_function
Plugin not supported
/bin/bash: line 4: 20630 Segmentation fault      (core dumped) ${dir}$tst
FAIL: farsight_test_rtp_5
===================
6 of 6 tests failed
===================
make[2]: *** [check-TESTS] Error 1
make[2]: Leaving directory `/home/ubuntu/Desktop/farsight-0.1.3.1/tests'
make[1]: *** [check-am] Error 2
make[1]: Leaving directory `/home/ubuntu/Desktop/farsight-0.1.3.1/tests'
make: *** [check-recursive] Error 1





I think this has something to do with it, this is what at the end of messages after "./configure":
configure: *** Plug-ins that will be built:
        rtp

configure: *** Plug-ins that will NOT be built:
        msnavconf
        msnwebcam
        yahoowebcam

ubuntu@ubuntu:~/Desktop/farsight-0.1.3.1$ make check

---

