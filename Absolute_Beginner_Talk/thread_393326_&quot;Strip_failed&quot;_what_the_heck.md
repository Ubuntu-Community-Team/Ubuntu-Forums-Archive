---
title: "&quot;Strip failed&quot;: what the heck?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Starks on 2007-03-25
Can somebody tell me why this won't finish properly?

```
This package will be built according to these values: 

0 -  Maintainer: [ eric@freelance ]
1 -  Summary: [ MPlayer Custom ]
2 -  Name:    [ mplayer-checkout-2007-03 ]
3 -  Version: [ 2:1.0~rc1-0ubuntu8 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ mplayer-checkout-2007-03-25 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
install -d /usr/local/bin
install -d /usr/local/share/mplayer
install -d /usr/local/man/man1
install -d /usr/local/etc/mplayer
if test -f /usr/local/etc/mplayer/codecs.conf ; then mv -f /usr/local/etc/mplayer/codecs.conf /usr/local/etc/mplayer/codecs.conf.old ; fi
make -C libvo libvo.a
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libvo'
make[1]: `libvo.a' is up to date.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libvo'
make -C libao2
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libao2'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libao2'
make -C input
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/input'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/input'
make -C libdha
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libdha'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libdha'
make -C vidix
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/vidix'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/vidix'
make -C vidix/drivers
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/vidix/drivers'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/vidix/drivers'
make -C Gui
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/Gui'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/Gui'
make -C libmpcodecs
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libmpcodecs'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libmpcodecs'
make -C libaf
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libaf'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libaf'
make -C libmpdemux libmpdemux.a
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libmpdemux'
make[1]: `libmpdemux.a' is up to date.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libmpdemux'
make -C stream
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/stream'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/stream'
make -C libswscale LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libswscale'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libswscale'
make -C libvo libosd.a
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libvo'
make[1]: `libosd.a' is up to date.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libvo'
make -C libavformat LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libavformat'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libavformat'
make -C libavcodec LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libavcodec'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libavcodec'
make -C libavutil LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libavutil'
make -C loader
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/loader'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/loader'
make -C mp3lib
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/mp3lib'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/mp3lib'
make -C liba52
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/liba52'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/liba52'
make -C libmpeg2
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libmpeg2'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libmpeg2'
make -C libfaad2
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libfaad2'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libfaad2'
make -C dvdread
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/dvdread'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/dvdread'
make -C libdvdcss
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libdvdcss'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libdvdcss'
make -C libass
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/libass'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/libass'
make -C osdep
make[1]: Entering directory `/home/eric/src/mplayer-checkout-2007-03-25/osdep'
make[1]: Nothing to be done for `libs'.
make[1]: Leaving directory `/home/eric/src/mplayer-checkout-2007-03-25/osdep'
install -m 755 -s mplayer /usr/local/bin
strip: could not create temporary file to hold stripped copy of '/usr/local/bin/mplayer'
install: strip failed
make: *** [install-mplayer] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

---

### Post by Starks on 2007-03-25
never mind, i think i figured it out.

---

### Post by Ace2016 on 2007-04-21
How did you fix the error, the only thing i could to get it to work was to run make install before i did checkinstall, is there a better way? is there a problem somewhere else which is causing it because it used to work fine in dapper?

---

