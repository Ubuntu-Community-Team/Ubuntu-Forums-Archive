---
title: "*sigh* Another failed attempt at compiling"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-09
What am I doing wrong? :confused:

```
erik@erik-desktop:~/Desktop$ cd last.fm-1.4.2.58240/
erik@erik-desktop:~/Desktop/last.fm-1.4.2.58240$ ./configure
==> Last.fm Configure 
==> Checking for qmake... 
==> Checking the installed version of Qt is correct... 
./configure: line 40: -v: command not found
Your version of Qt seems to be too old, we require Qt 4.3 or above.

It is possible you have Qt3 and Qt4 both installed. Locate your qt4 installation
and ensure it is placed first in the path, eg:

        PATH=/opt/qt4/bin:$PATH ./configure

However this configure script is very basic, perhaps we got it wrong..
Try typing the following, perhaps it will build for you :)

        qmake -config release && make
erik@erik-desktop:~/Desktop/last.fm-1.4.2.58240$ ./configure && make
==> Last.fm Configure 
==> Checking for qmake... 
==> Checking the installed version of Qt is correct... 
./configure: line 40: -v: command not found
Your version of Qt seems to be too old, we require Qt 4.3 or above.

It is possible you have Qt3 and Qt4 both installed. Locate your qt4 installation
and ensure it is placed first in the path, eg:

        PATH=/opt/qt4/bin:$PATH ./configure

However this configure script is very basic, perhaps we got it wrong..
Try typing the following, perhaps it will build for you :)

        qmake -config release && make
make: *** No targets specified and no makefile found.  Stop.
erik@erik-desktop:~/Desktop/last.fm-1.4.2.58240$ ls
bin        configure  definitions.pro.inc  LastFM.pro  README  src
ChangeLog  COPYING    i18n                 patches     res     tests
erik@erik-desktop:~/Desktop/last.fm-1.4.2.58240$ 

```

---

### Post by frup on 2008-01-09
Seems to need QT4 not QT3 ...

---

### Post by 449 on 2008-01-09
> **frup said:**
> Seems to need QT4 not QT3 ...

I installed it from Synaptic...

I think I might of missed some.

I'll try those and hope for the best.

---

### Post by 449 on 2008-01-09
```
/usr/bin/ld: cannot find -lfftw3f
collect2: ld returned 1 exit status
make[1]: *** [../../bin/libLastFmFingerprint.so.1.0.0] Error 1
make[1]: Leaving directory `/home/erik/Desktop/last.fm-1.4.2.58240/src/libFingerprint'
make: *** [sub-src-libFingerprint-make_default-ordered] Error 2
erik@erik-desktop:~/Desktop/last.fm-1.4.2.58240$ 


```

---

### Post by RomeReactor on 2008-01-09
Hi. Have you installed build-essential and libqt4-dev?
```
sudo apt-get install build-essential libqt4-dev
```

Try running it as it suggested:
```
qmake -config release && make
```

EDIT: There's also a [Gutsy .deb package]("http://cdn.last.fm/client/Linux/lastfm_1.4.2.58240_i386.deb") in their [downloads page]("http://www.last.fm/download/").

---

### Post by Kevin Fischer on 2008-01-12
I'm getting the same error:

cd src/libFingerprint/ && make -f Makefile 
make[1]: Entering directory `/home/kfischer/bin/last.fm-1.4.2.58240/src/libFingerprint'
make[1]: *** No rule to make target `FingerprintCollector.cpp', needed by `../../build/LastFmFingerprint/release/FingerprintCollector.o'.  Stop.
make[1]: Leaving directory `/home/kfischer/bin/last.fm-1.4.2.58240/src/libFingerprint'
make: *** [sub-src-libFingerprint-make_default-ordered] Error 2


I can't use the .deb package because I'm on a 64-bit machine.

Also, I have installed all the libraries (except I couldn't find alsa-lib?)

---

### Post by 449 on 2008-01-13
> **Kevin Fischer said:**
> I'm getting the same error:

cd src/libFingerprint/ && make -f Makefile 
make[1]: Entering directory `/home/kfischer/bin/last.fm-1.4.2.58240/src/libFingerprint'
make[1]: *** No rule to make target `FingerprintCollector.cpp', needed by `../../build/LastFmFingerprint/release/FingerprintCollector.o'.  Stop.
make[1]: Leaving directory `/home/kfischer/bin/last.fm-1.4.2.58240/src/libFingerprint'
make: *** [sub-src-libFingerprint-make_default-ordered] Error 2


I can't use the .deb package because I'm on a 64-bit machine.

Also, I have installed all the libraries (except I couldn't find alsa-lib?)

I ended up just giving up and downloading from synaptic. You on the other hand don't have that option. Have you tried googling for some install instructions?

---

### Post by Brucevdk on 2008-07-06
Took me a while but I finally managed to compile the Last.fm Player. I wrote a little HOWTO at the end of this post. But first let's get some replies of the way. 

> **449 said:**
> /usr/bin/ld: cannot find -lfftw3f

You're missing *fftw3-dev*, install it using: *sudo apt-get install fftw3-dev*

> **Kevin Fischer said:**
> I'm getting the same error:

Actually it's not the same error, in your case the error points to a missing FingerprintCollector.cpp. That file is missing from the 1.4.2.58240 version tarball, which is also the one that is most prominently offered through the [the Last.fm download page](http://www.last.fm/download/) (by way of the download button). Somebody should probably tell them this, since the latest version is listed on the same page (but at the bottom).

[SIZE="4"]A little HOWTO[/SIZE]

First off, if you have both qt3 and qt4 libraries installed, most importantly libqt4-dev and qt3-dev-tools, you'll have to select the qmake for qt4 (do this using *sudo update-alternatives --config qmake*).

Now if you look down on the download page you'll notice a tarball for [1.5.1.31879](http://cdn.last.fm/client/src/last.fm-1.5.1.31879.tar.bz2), even though this tarball isn't compilable it's easy enough to make the required change.

It turns out that libfplib has its target set to debug (./src/libFingerprint/fplib/pro_qmake/Makefile.fplib: TARGET = libfplib_debug.a) however the Makefile for libFingerprint still points to libfplib.a (./src/libFingerprint/Makefile).

Just change the line */build/fplib/libfplib.a* to */build/fplib/libfplib_debug.a* in *./src/libFingerprint/Makefile* and be done with it.

Run it using ./bin/last.fm.sh (not ./bin/last.fm) because this shell script sets the LD_LIBRARY_PATH for you.

Some thanks to one of the latest ["The Last.fm Player Won't Compile... Again"](http://www.last.fm/forum/34905/_/365027) threads over at Last.fm for confirming my suspensions regarding libfplib.

---

