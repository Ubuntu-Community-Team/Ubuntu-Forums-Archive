---
title: "Help running USB Creative Zen Player"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by m0rph on 2007-01-19
Howdy All, After spending the last week reading many Thread's and following many different installs and compiles setting up Gnomad2 and Amarok for my creative Zen Vision: M USB Mp3 player with Ubunto 6.06 it is with great dissipointment that I still get the following messege when running gnomad 2 from the terminal;

" No jukeboxes found on USB bus "

My last resort is to post this Thread in the hope that someone can help.
I would just like to access the Hard drive and drop files and remove files that is all.

When typing lsusb
Bus 004 Device 005: ID 041e:413e Creative Technology, Ltd
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

I look forward to any assistance or walkthru you can provide............ ](*,)

---

### Post by riven0 on 2007-01-19
Does your media player automount at all? Do you see it appear on the desktop?

If not, plug it in, wait a moment and then post the results of this:

> sudo fdisk -l

---

### Post by schwascore on 2007-01-19
The Zen Vision is a MTP device, which does not automatically mount to Ubuntu.  You need to have libmtp installed and compile Amarok specifically to use libmtp.  If you want to drag and drop files (other than music), make sure you have enabled the Zen Vision's built in USB disk mode.  Otherwise, here is what I did to get my Zen Vision working with Amarok.

1) Get the Amarok-svn install script.  [Click Here]("http://kde-apps.org/content/show.php?content=27313").
2) Make sure you have installed libusb and [libmtp]("http://downloads.sourceforge.net/libmtp/libmtp-0.1.3.tar.gz?modtime=1168984506&big_mirror=0") installed.  Libusb is available through apt-get or synaptic, install both the main package and the libusb-dev package.
3) You will also need subversion, python and it's dev package.
4) Run the script in your home directory.
5)When the installer asks if there are any extra configure options click "yes" and then type in: ```
--with-libmtp
```.
6) If there are any failures in the install, read the error message and install any missing dependencies.
7) Start up Amarok and configure it with your music collection.
8) Click on Settings --> Configure Amarok , then on Media Devices at the bottom left.
9) Plug in your Zen Vision (make sure it's not in USB mode) and then click on "Autodetect Devices" and it should detect it just fine.

Good luck, my vision is working just fine.  If you have any other problems just post!

---

### Post by m0rph on 2007-01-19
riven0 - No Automount no Icon

schwascore - Before i try your steps I am currently redoing 
[http://ubuntuforums.org/showthread.php?t=199250](http://ubuntuforums.org/showthread.php?t=199250)
And i'm at Step 12. Compile libnjb

The following is what i get;

po" -c -o njbtime.lo njbtime.c; \
        then mv -f ".deps/njbtime.Tpo" ".deps/njbtime.Plo"; else rm -f ".deps/nj btime.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -Wall -Wmissing-prototypes -MT njbtime. lo -MD -MP -MF .deps/njbtime.Tpo -c njbtime.c  -fPIC -DPIC -o .libs/njbtime.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -Wall -Wmissing-prototypes -MT njbtime. lo -MD -MP -MF .deps/njbtime.Tpo -c njbtime.c -o njbtime.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -g -O2 -Wall -Wmissing-prototypes -MT protocol3.lo -MD -MP -MF ".deps/protoco l3.Tpo" -c -o protocol3.lo protocol3.c; \
        then mv -f ".deps/protocol3.Tpo" ".deps/protocol3.Plo"; else rm -f ".dep s/protocol3.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -Wall -Wmissing-prototypes -MT protocol 3.lo -MD -MP -MF .deps/protocol3.Tpo -c protocol3.c  -fPIC -DPIC -o .libs/protoc ol3.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -Wall -Wmissing-prototypes -MT protocol 3.lo -MD -MP -MF .deps/protocol3.Tpo -c protocol3.c -o protocol3.o >/dev/null 2> &1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -g -O2 -Wall -Wmissing-prototypes -MT unicode.lo -MD -MP -MF ".deps/unicode.T po" -c -o unicode.lo unicode.c; \
        then mv -f ".deps/unicode.Tpo" ".deps/unicode.Plo"; else rm -f ".deps/un icode.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -Wall -Wmissing-prototypes -MT unicode. lo -MD -MP -MF .deps/unicode.Tpo -c unicode.c  -fPIC -DPIC -o .libs/unicode.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -Wall -Wmissing-prototypes -MT unicode. lo -MD -MP -MF .deps/unicode.Tpo -c unicode.c -o unicode.o >/dev/null 2>&1
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2 -Wall -Wmissing-prototypes  -o libnjb.la -rpath /usr/lib -version-info 6:0:1  base.lo ioutil.lo protocol.lo  procedure.lo byteorder.lo playlist.lo usb_io.lo njb_error.lo datafile.lo songid .lo eax.lo njbtime.lo protocol3.lo unicode.lo  -lusb
rm -fr  .libs/libnjb.a .libs/libnjb.la .libs/libnjb.lai .libs/libnjb.so .libs/li bnjb.so.5 .libs/libnjb.so.5.1.0
gcc -shared  .libs/base.o .libs/ioutil.o .libs/protocol.o .libs/procedure.o .lib s/byteorder.o .libs/playlist.o .libs/usb_io.o .libs/njb_error.o .libs/datafile.o  .libs/songid.o .libs/eax.o .libs/njbtime.o .libs/protocol3.o .libs/unicode.o  / usr/lib/libusb.so  -Wl,-soname -Wl,libnjb.so.5 -o .libs/libnjb.so.5.1.0
(cd .libs && rm -f libnjb.so.5 && ln -s libnjb.so.5.1.0 libnjb.so.5)
(cd .libs && rm -f libnjb.so && ln -s libnjb.so.5.1.0 libnjb.so)
ar cru .libs/libnjb.a  base.o ioutil.o protocol.o procedure.o byteorder.o playli st.o usb_io.o njb_error.o datafile.o songid.o eax.o njbtime.o protocol3.o unicod e.o
ranlib .libs/libnjb.a
creating libnjb.la
(cd .libs && rm -f libnjb.la && ln -s ../libnjb.la libnjb.la)
make[2]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5/src'
Making all in sample
make[2]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5/sample'
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT delfile.o -MD -MP -MF ".deps/delfile.Tpo" -c -o delfile.o delfile.c; \
        then mv -f ".deps/delfile.Tpo" ".deps/delfile.Po"; else rm -f ".deps/del file.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o delfile  delfile.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/delfile delfile.o  ../sr c/.libs/libnjb.so /usr/lib/libusb.so
creating delfile
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT deltr.o -MD -MP -MF ".deps/deltr.Tpo" -c -o deltr.o deltr.c; \
        then mv -f ".deps/deltr.Tpo" ".deps/deltr.Po"; else rm -f ".deps/deltr.T po"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o deltr  deltr.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/deltr deltr.o  ../src/.l ibs/libnjb.so /usr/lib/libusb.so
creating deltr
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT dumpeax.o -MD -MP -MF ".deps/dumpeax.Tpo" -c -o dumpeax.o dumpeax.c; \
        then mv -f ".deps/dumpeax.Tpo" ".deps/dumpeax.Po"; else rm -f ".deps/dum peax.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o dumpeax  dumpeax.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/dumpeax dumpeax.o  ../sr c/.libs/libnjb.so /usr/lib/libusb.so
creating dumpeax
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT dumptime.o -MD -MP -MF ".deps/dumptime.Tpo" -c -o dumptime.o dumptime.c; \
        then mv -f ".deps/dumptime.Tpo" ".deps/dumptime.Po"; else rm -f ".deps/d umptime.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o dumptime  dumptime.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/dumptime dumptime.o  ../ src/.libs/libnjb.so /usr/lib/libusb.so
creating dumptime
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT files.o -MD -MP -MF ".deps/files.Tpo" -c -o files.o files.c; \
        then mv -f ".deps/files.Tpo" ".deps/files.Po"; else rm -f ".deps/files.T po"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o files  files.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/files files.o  ../src/.l ibs/libnjb.so /usr/lib/libusb.so
creating files
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT fwupgrade.o -MD -MP -MF ".deps/fwupgrade.Tpo" -c -o fwupgrade.o fwupgrade. c; \
        then mv -f ".deps/fwupgrade.Tpo" ".deps/fwupgrade.Po"; else rm -f ".deps /fwupgrade.Tpo"; exit 1; fi
fwupgrade.c: In function ‘main’:
fwupgrade.c:349: warning: pointer targets in passing argument 3 of ‘dexor_fw_ima ge’ differ in signedness
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o fwupgrade  fwupgrade.o ../src/libnjb.la -lz -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/fwupgrade fwupgrade.o  . ./src/.libs/libnjb.so -lz /usr/lib/libusb.so
creating fwupgrade
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT getfile.o -MD -MP -MF ".deps/getfile.Tpo" -c -o getfile.o getfile.c; \
        then mv -f ".deps/getfile.Tpo" ".deps/getfile.Po"; else rm -f ".deps/get file.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o getfile  getfile.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/getfile getfile.o  ../sr c/.libs/libnjb.so /usr/lib/libusb.so
creating getfile
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT getowner.o -MD -MP -MF ".deps/getowner.Tpo" -c -o getowner.o getowner.c; \
        then mv -f ".deps/getowner.Tpo" ".deps/getowner.Po"; else rm -f ".deps/g etowner.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o getowner  getowner.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/getowner getowner.o  ../ src/.libs/libnjb.so /usr/lib/libusb.so
creating getowner
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT gettr.o -MD -MP -MF ".deps/gettr.Tpo" -c -o gettr.o gettr.c; \
        then mv -f ".deps/gettr.Tpo" ".deps/gettr.Po"; else rm -f ".deps/gettr.T po"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o gettr  gettr.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/gettr gettr.o  ../src/.l ibs/libnjb.so /usr/lib/libusb.so
creating gettr
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT getusage.o -MD -MP -MF ".deps/getusage.Tpo" -c -o getusage.o getusage.c; \
        then mv -f ".deps/getusage.Tpo" ".deps/getusage.Po"; else rm -f ".deps/g etusage.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o getusage  getusage.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/getusage getusage.o  ../ src/.libs/libnjb.so /usr/lib/libusb.so
creating getusage
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT handshake.o -MD -MP -MF ".deps/handshake.Tpo" -c -o handshake.o handshake. c; \
        then mv -f ".deps/handshake.Tpo" ".deps/handshake.Po"; else rm -f ".deps /handshake.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o handshake  handshake.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/handshake handshake.o  . ./src/.libs/libnjb.so /usr/lib/libusb.so
creating handshake
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT pl.o -MD -MP -MF ".deps/pl.Tpo" -c -o pl.o pl.c; \
        then mv -f ".deps/pl.Tpo" ".deps/pl.Po"; else rm -f ".deps/pl.Tpo"; exit  1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o pl  pl.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/pl pl.o  ../src/.libs/li bnjb.so /usr/lib/libusb.so
creating pl
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT play.o -MD -MP -MF ".deps/play.Tpo" -c -o play.o play.c; \
        then mv -f ".deps/play.Tpo" ".deps/play.Po"; else rm -f ".deps/play.Tpo" ; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o play  play.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/play play.o  ../src/.lib s/libnjb.so /usr/lib/libusb.so
creating play
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT playlists.o -MD -MP -MF ".deps/playlists.Tpo" -c -o playlists.o playlists. c; \
        then mv -f ".deps/playlists.Tpo" ".deps/playlists.Po"; else rm -f ".deps /playlists.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o playlists  playlists.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/playlists playlists.o  . ./src/.libs/libnjb.so /usr/lib/libusb.so
creating playlists
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT sendfile.o -MD -MP -MF ".deps/sendfile.Tpo" -c -o sendfile.o sendfile.c; \
        then mv -f ".deps/sendfile.Tpo" ".deps/sendfile.Po"; else rm -f ".deps/s endfile.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o sendfile  sendfile.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/sendfile sendfile.o  ../ src/.libs/libnjb.so /usr/lib/libusb.so
creating sendfile
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT sendtr.o -MD -MP -MF ".deps/sendtr.Tpo" -c -o sendtr.o sendtr.c; \
        then mv -f ".deps/sendtr.Tpo" ".deps/sendtr.Po"; else rm -f ".deps/sendt r.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o sendtr  sendtr.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/sendtr sendtr.o  ../src/ .libs/libnjb.so /usr/lib/libusb.so
creating sendtr
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT setowner.o -MD -MP -MF ".deps/setowner.Tpo" -c -o setowner.o setowner.c; \
        then mv -f ".deps/setowner.Tpo" ".deps/setowner.Po"; else rm -f ".deps/s etowner.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o setowner  setowner.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/setowner setowner.o  ../ src/.libs/libnjb.so /usr/lib/libusb.so
creating setowner
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT setpbm.o -MD -MP -MF ".deps/setpbm.Tpo" -c -o setpbm.o setpbm.c; \
        then mv -f ".deps/setpbm.Tpo" ".deps/setpbm.Po"; else rm -f ".deps/setpb m.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o setpbm  setpbm.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/setpbm setpbm.o  ../src/ .libs/libnjb.so /usr/lib/libusb.so
creating setpbm
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT settime.o -MD -MP -MF ".deps/settime.Tpo" -c -o settime.o settime.c; \
        then mv -f ".deps/settime.Tpo" ".deps/settime.Po"; else rm -f ".deps/set time.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o settime  settime.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/settime settime.o  ../sr c/.libs/libnjb.so /usr/lib/libusb.so
creating settime
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT tagtr.o -MD -MP -MF ".deps/tagtr.Tpo" -c -o tagtr.o tagtr.c; \
        then mv -f ".deps/tagtr.Tpo" ".deps/tagtr.Po"; else rm -f ".deps/tagtr.T po"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o tagtr  tagtr.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/tagtr tagtr.o  ../src/.l ibs/libnjb.so /usr/lib/libusb.so
creating tagtr
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -g -O2 -Wall -Wmissing-prototype s -MT tracks.o -MD -MP -MF ".deps/tracks.Tpo" -c -o tracks.o tracks.c; \
        then mv -f ".deps/tracks.Tpo" ".deps/tracks.Po"; else rm -f ".deps/track s.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -I../src -g -O2 -Wall -Wmissing-prot otypes   -o tracks  tracks.o ../src/libnjb.la -lusb
gcc -I../src -g -O2 -Wall -Wmissing-prototypes -o .libs/tracks tracks.o  ../src/ .libs/libnjb.so /usr/lib/libusb.so
creating tracks
make[2]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5/sample'
Making all in doc
make[2]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5/doc'
make[2]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5'
make[2]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5'
make[1]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5'
m0rph@m0rph:~/gnomad_install/libnjb-2.2.5$ sudo checkinstall 
checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ root@m0rph ]
1 -  Summary: [ step12 ]
2 -  Name:    [ libnjb ]
3 -  Version: [ 2.2.5 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ libnjb-2.2.5 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5/src'
make[2]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5/src'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/sh ../libtool --mode=install /usr/bin/install -c  'libnjb.la' '/usr/lib/li bnjb.la'
/usr/bin/install -c .libs/libnjb.so.5.1.0 /usr/lib/libnjb.so.5.1.0
/usr/bin/install: setting permissions for `/usr/lib/libnjb.so.5.1.0': No such fi le or directory
(cd /usr/lib && rm -f libnjb.so.5 && ln -s libnjb.so.5.1.0 libnjb.so.5)
(cd /usr/lib && rm -f libnjb.so && ln -s libnjb.so.5.1.0 libnjb.so)
/usr/bin/install -c .libs/libnjb.lai /usr/lib/libnjb.la
/usr/bin/install: setting permissions for `/usr/lib/libnjb.la': No such file or directory
/usr/bin/install -c .libs/libnjb.a /usr/lib/libnjb.a
/usr/bin/install: setting permissions for `/usr/lib/libnjb.a': No such file or d irectory
ranlib /usr/lib/libnjb.a
chmod 644 /usr/lib/libnjb.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/include" || mkdir -p -- "/usr/include"
 /usr/bin/install -c -m 644 'libnjb.h' '/usr/include/libnjb.h'
/usr/bin/install: setting permissions for `/usr/include/libnjb.h': No such file or directory
make[2]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5/src'
make[1]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5/src'
Making install in sample
make[1]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5/sample'
make[2]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5/sample'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'delfile' '/usr/bin/njb- delfile'
/usr/bin/install -c .libs/delfile /usr/bin/njb-delfile
/usr/bin/install: setting permissions for `/usr/bin/njb-delfile': No such file o r directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'deltr' '/usr/bin/njb-de ltr'
/usr/bin/install -c .libs/deltr /usr/bin/njb-deltr
/usr/bin/install: setting permissions for `/usr/bin/njb-deltr': No such file or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'dumpeax' '/usr/bin/njb- dumpeax'
/usr/bin/install -c .libs/dumpeax /usr/bin/njb-dumpeax
/usr/bin/install: setting permissions for `/usr/bin/njb-dumpeax': No such file o r directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'dumptime' '/usr/bin/njb -dumptime'
/usr/bin/install -c .libs/dumptime /usr/bin/njb-dumptime
/usr/bin/install: setting permissions for `/usr/bin/njb-dumptime': No such file or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'files' '/usr/bin/njb-fi les'
/usr/bin/install -c .libs/files /usr/bin/njb-files
/usr/bin/install: setting permissions for `/usr/bin/njb-files': No such file or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'fwupgrade' '/usr/bin/nj b-fwupgrade'
/usr/bin/install -c .libs/fwupgrade /usr/bin/njb-fwupgrade
/usr/bin/install: setting permissions for `/usr/bin/njb-fwupgrade': No such file  or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'getfile' '/usr/bin/njb- getfile'
/usr/bin/install -c .libs/getfile /usr/bin/njb-getfile
/usr/bin/install: setting permissions for `/usr/bin/njb-getfile': No such file o r directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'getowner' '/usr/bin/njb -getowner'
/usr/bin/install -c .libs/getowner /usr/bin/njb-getowner
/usr/bin/install: setting permissions for `/usr/bin/njb-getowner': No such file or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'gettr' '/usr/bin/njb-ge ttr'
/usr/bin/install -c .libs/gettr /usr/bin/njb-gettr
/usr/bin/install: setting permissions for `/usr/bin/njb-gettr': No such file or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'getusage' '/usr/bin/njb -getusage'
/usr/bin/install -c .libs/getusage /usr/bin/njb-getusage
/usr/bin/install: setting permissions for `/usr/bin/njb-getusage': No such file or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'handshake' '/usr/bin/nj b-handshake'
/usr/bin/install -c .libs/handshake /usr/bin/njb-handshake
/usr/bin/install: setting permissions for `/usr/bin/njb-handshake': No such file  or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'pl' '/usr/bin/njb-pl'
/usr/bin/install -c .libs/pl /usr/bin/njb-pl
/usr/bin/install: setting permissions for `/usr/bin/njb-pl': No such file or dir ectory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'play' '/usr/bin/njb-pla y'
/usr/bin/install -c .libs/play /usr/bin/njb-play
/usr/bin/install: setting permissions for `/usr/bin/njb-play': No such file or d irectory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'playlists' '/usr/bin/nj b-playlists'
/usr/bin/install -c .libs/playlists /usr/bin/njb-playlists
/usr/bin/install: setting permissions for `/usr/bin/njb-playlists': No such file  or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'sendfile' '/usr/bin/njb -sendfile'
/usr/bin/install -c .libs/sendfile /usr/bin/njb-sendfile
/usr/bin/install: setting permissions for `/usr/bin/njb-sendfile': No such file or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'sendtr' '/usr/bin/njb-s endtr'
/usr/bin/install -c .libs/sendtr /usr/bin/njb-sendtr
/usr/bin/install: setting permissions for `/usr/bin/njb-sendtr': No such file or  directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'setowner' '/usr/bin/njb -setowner'
/usr/bin/install -c .libs/setowner /usr/bin/njb-setowner
/usr/bin/install: setting permissions for `/usr/bin/njb-setowner': No such file or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'setpbm' '/usr/bin/njb-s etpbm'
/usr/bin/install -c .libs/setpbm /usr/bin/njb-setpbm
/usr/bin/install: setting permissions for `/usr/bin/njb-setpbm': No such file or  directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'settime' '/usr/bin/njb- settime'
/usr/bin/install -c .libs/settime /usr/bin/njb-settime
/usr/bin/install: setting permissions for `/usr/bin/njb-settime': No such file o r directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'tagtr' '/usr/bin/njb-ta gtr'
/usr/bin/install -c .libs/tagtr /usr/bin/njb-tagtr
/usr/bin/install: setting permissions for `/usr/bin/njb-tagtr': No such file or directory
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'tracks' '/usr/bin/njb-t racks'
/usr/bin/install -c .libs/tracks /usr/bin/njb-tracks
/usr/bin/install: setting permissions for `/usr/bin/njb-tracks': No such file or  directory
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5/sample'
make[1]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5/sample'
Making install in doc
make[1]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5/doc'
make[2]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5/doc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5/doc'
make[1]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5/doc'
make[1]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5'
make[2]: Entering directory `/home/m0rph/gnomad_install/libnjb-2.2.5'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/etc/hotplug/usb" || mkdir -p -- "/etc/hotplug/usb"
 /usr/bin/install -c -m 644 'nomad.usermap' '/etc/hotplug/usb/nomad.usermap'
/usr/bin/install: setting permissions for `/etc/hotplug/usb/nomad.usermap': No s uch file or directory
 /usr/bin/install -c -m 644 'nomadjukebox' '/etc/hotplug/usb/nomadjukebox'
/usr/bin/install: setting permissions for `/etc/hotplug/usb/nomadjukebox': No su ch file or directory
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'libnjb.pc' '/usr/lib/pkgconfig/libnjb.pc'
/usr/bin/install: setting permissions for `/usr/lib/pkgconfig/libnjb.pc': No suc h file or directory
make[2]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5'
make[1]: Leaving directory `/home/m0rph/gnomad_install/libnjb-2.2.5'

======================== Installation successful ==========================

Copying documentation directory...
./
./AUTHORS
./ChangeLog
./FAQ
./HACKING
./INSTALL
./LICENSE
./README
./doc/
./doc/Makefile.am
./doc/examples.h
./doc/Makefile.in
./doc/Doxyfile.in
./doc/mainpage.h
./doc/Doxyfile
./doc/Makefile

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]: n

Erasing temporary files...OK

Deleting temp dir...OK


Why is this failing ?????????
I will try your steps schwascore but the above may show my problem
as without libnjb i cannot continue to install gnome2.

I await your help please........ :(

---

### Post by schwascore on 2007-01-19
Make sure that synaptic is not running when you run checkinstall as root.  If that doesn't work, hit "y" to see the log file and post that so we can take a look at the errors.

If you want gnomad2 to work, continue to follow the instructions that you linked to, but just so you know, you do not need libnjb or gnomad2 installed for the Vision to work with Amarok.  

You will need gnomad2 if you want to transfer video and photos to the device, however there is not full support for organizing photos and videos.  It's kind of annoying, really, because you can't create folders for the photos or videos and they show up alphabetically in gnomad2 so they are all mixed in with your music files.  It's not a problem with gnomad2, but rather with Microsoft and their MTP standard - they only allow the "basic" commands to be used in open source software so many features are missing.

Bottom Line:  If you want to transfer videos and photos, keep working on gnomad2.  If you only care about music, just go for Amarok.

Keep us posted!

EDIT:  I am doing a clean install of gnomad2 in the hope of duplicating your problem.

---

### Post by schwascore on 2007-01-20
I think I found something.

I had the same problem compiling libnjb.  Turns out I had another version of libnjb installed, so all I did was remove it through synaptic and then ran checkinstall again and it worked.

This might be the same problem for you, if you post the error from checkinstall I'll be able to tell.

---

### Post by m0rph on 2007-01-20
Thanks for the help schwascore  
gnomad2
After running checkinstall
it now has
**********************************************************************

 Done. The new package has been installed and saved to

 /home/m0rph/gnomad_install/libnjb-2.2.5/libnjb_2.2.5-1_i386.deb

 You can remove it from your system anytime using:

      dpkg -r libnjb

**********************************************************************

I have moved onto Step 15 with now the following error;

**********************************************************************

 Done. The new package has been installed and saved to

 /home/m0rph/gnomad_install/libnjb-2.2.5/libnjb_2.2.5-1_i386.deb

 You can remove it from your system anytime using:

      dpkg -r libnjb

**********************************************************************

m0rph@m0rph:~/gnomad_install/libnjb-2.2.5$ cd ..
m0rph@m0rph:~/gnomad_install$ cd gnomad2-2.8.9
m0rph@m0rph:~/gnomad_install/gnomad2-2.8.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GN... yes
checking for gtk+-2.0 >= 2.6.0... checking for TAG... yes
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
checking for egrep... grep -E
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
checking id3tag.h usability... yes
checking id3tag.h presence... yes
checking for id3tag.h... yes
checking for MTP... yes
checking libmtp.h usability... yes
checking libmtp.h presence... yes
checking for libmtp.h... yes
checking for intltool >= 0.35.0... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for chdir... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating doc/Makefile
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

gnomad2 2.8.9
Configuration :
---------------

 Source code location .: .
 C Preprocessor .......: gcc -E
 C Compiler ...........: gcc -g -O2
 C Linker .............: gcc
 GTK+ version .........: 2.8.20
 libgnomeui version....: NOT USED
 libnjb version........: 2.2.5
 libmtp version........: 0.1.1
 id3tag version........: 0.15.0b
 Install path .........: /usr/local

 Now type 'make' to build gnomad2 2.8.9,
 and then 'make install' for installation.

m0rph@m0rph:~/gnomad_install/gnomad2-2.8.9$ sudo make
Making all in src
make[1]: Entering directory `/home/m0rph/gnomad_install/gnomad2-2.8.9/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"gnomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT gnomad2.o -MD -MP -MF ".deps/gnomad2.Tpo" -c -o gnomad2.o gnomad2.c; \
        then mv -f ".deps/gnomad2.Tpo" ".deps/gnomad2.Po"; else rm -f ".deps/gnomad2.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"gnomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o jukebox.o jukebox.c; \
        then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/jukebox.Tpo"; exit 1; fi
jukebox.c: In function ‘jb2hd_thread’:
jukebox.c:1854: warning: assignment makes pointer from integer without a cast
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"gnomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT editmeta.o -MD -MP -MF ".deps/editmeta.Tpo" -c -o editmeta.o editmeta.c; \
        then mv -f ".deps/editmeta.Tpo" ".deps/editmeta.Po"; else rm -f ".deps/editmeta.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"gnomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT playlists.o -MD -MP -MF ".deps/playlists.Tpo" -c -o playlists.o playlists.c; \
        then mv -f ".deps/playlists.Tpo" ".deps/playlists.Po"; else rm -f ".deps/playlists.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"gnomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT xfer.o -MD -MP -MF ".deps/xfer.Tpo" -c -o xfer.o xfer.c; \
        then mv -f ".deps/xfer.Tpo" ".deps/xfer.Po"; else rm -f ".deps/xfer.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"gnomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT data.o -MD -MP -MF ".deps/data.Tpo" -c -o data.o data.c; \
        then mv -f ".deps/data.Tpo" ".deps/data.Po"; else rm -f ".deps/data.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"gnomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT player.o -MD -MP -MF ".deps/player.Tpo" -c -o player.o player.c; \
        then mv -f ".deps/player.Tpo" ".deps/player.Po"; else rm -f ".deps/player.Tpo"; exit 1; fi
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o -pthread -lgthread-2.0 -lnjb -lusb -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -lmtp -lusb
jukebox.o: In function `hd2jb_thread':/home/m0rph/gnomad_install/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':jukebox.c:(.text+0x20fa): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/m0rph/gnomad_install/gnomad2-2.8.9/src'
make: *** [all-recursive] Error 1
m0rph@m0rph:~/gnomad_install/gnomad2-2.8.9$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ root@m0rph ]
1 -  Summary: [ stuff ]
2 -  Name:    [ gnomad2 ]
3 -  Version: [ 2.8.9 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ gnomad2-2.8.9 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/m0rph/gnomad_install/gnomad2-2.8.9/src'
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o -pthread -lgthread-2.0 -lnjb -lusb -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -lmtp -lusb
jukebox.o: In function `hd2jb_thread':/home/m0rph/gnomad_install/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':jukebox.c:(.text+0x20fa): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/m0rph/gnomad_install/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
What is the problem now i wonder ?

I have also started your steps on
amarok
I'm upto your step 4) Run the script in your home directory.
What do I type once in my home directory to run this script i downloaded ? =D> 

I await your reply to both of the above setups.......

---

### Post by schwascore on 2007-01-20
First of all, to run the Amarok script, type the following lines:
```
mv 27313-amarok-svn.sh amarok-svn.sh
chmod 755 amarok-svn.sh
./amarok-svn.sh 
```

Also, I tried installing gnomad2 myself and I have the same error... very very strange.  It seems as though gnomad2 does not like one of the commands associated with libmtp.  I tried installing three different versions of libmtp with no luck.  This is about as far as I can help you with this problem... If I figure it out I will let you know but as of right now I have no idea on this one.  I'll  be around for a little while more tonight, so just post again if you need more help with Amarok.  In the mean time I'll try to figure out gnomad2's problem!

---

### Post by m0rph on 2007-01-20
okay on wth the Amarok steps then.

after typing what you said it says;

m0rph@m0rph:~$ mv 27313-amarok-svn.sh amarok-svn.sh
m0rph@m0rph:~$ chmod 755 amarok-svn.sh
m0rph@m0rph:~$ ./amarok-svn.sh

Amarok-svn (Version 3.1.1)
============================


ERROR: Amarok-svn requires kdialog, which wasn't found in your $PATH!
m0rph@m0rph:~$

Whats your thoughts ???
And thanks agin for the help as I look forward to using Amarok with my CZVM.....

---

### Post by schwascore on 2007-01-20
ah, sorry that's my bad.  I forgot the most important part!  you need a lot of KDE stuff.  Here is the best solution:

```
sudo apt-get install kdebase kdebase-dev libxine1 libxine1-dev ruby ruby1.8-dev python python2.4-dev
```

That will take care of most of the dependencies, especially all the KDE stuff and the Xine multimedia engine as well as the ruby and python dev packages.

I also posted a request for help to the gnomad2 guide we were working off of.  Hopefully someone has an answer to our problem!

---

### Post by m0rph on 2007-01-20
m0rph@m0rph:~$ sudo apt-get install kdebase kdebase-dev libxine1 libxine1-dev ruby ruby1.8-dev python python2.4-dev
Reading package lists... Done
Building dependency tree... Done
Package libxine1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine-main1
E: Package libxine1 has no installation candidate
m0rph@m0rph:~$



m0rph@m0rph:~$ ./amarok-svn.sh 
Amarok-svn (Version 3.1.1)
============================


ERROR: Amarok-svn requires kdialog, which wasn't found in your $PATH!


Are we missing libxine1 and that is why the above is still not  working ?

---

### Post by schwascore on 2007-01-20
Ok, I should have asked this a while ago, but which version of Ubuntu are you running?
Also, are your Multiverse and Universe repositories enabled?

---

### Post by m0rph on 2007-01-20
Ubuntu 6.06 LTS - the Dapper Drake - released in June 2006.
Multiverse and Universe repositories enabled? - YES.....

kdialog is part of kde manger i think ?........](*,) ](*,)

---

### Post by schwascore on 2007-01-20
Ok, i'm on Edgy, but for this it's the exact same.

kdialog is part of the backend of KDE.  It's not working because KDE was not installed because of the apt-get error with Xine.

Try this instead:

```
sudo apt-get install kdebase kdebase-dev gxine libxine-dev ruby ruby1.8-dev python python2.4-dev
```

FYI: this install will take a few minutes.  

I have to sign off for tonight, I'll be back on tomorrow afternoon though, EST time.  Everything should run fine once you get KDE and Xine installed, which should work with the code above.  Have a good one.

---

### Post by m0rph on 2007-01-20
ENTERED
sudo apt-get install kdebase kdebase-dev gxine libxine-dev ruby ruby1.8-dev python python2.4-dev


m0rph@m0rph:~$ ./amarok-svn.sh 
Amarok-svn (Version 3.1.1)
============================

Used configuration
--------------------
(Use --help to get information on how to change it.)

SVN server:                                     svn://anonsvn.kde.org
Language for localization and documentation:    en_US
Extra configuration options:                    --with-libmtp
Command for getting root privileges:            kdesu
Build ID:                                       Off
Build directory:                                /home/m0rph/amarok-svn
Clean source tree:                              Off

###################### #### ### ## ## ## # #

# 1/11 - Checking out base files.
Checked out revision 625452.

# 2/11 - Getting unsermake.
Unsermake downloaded by this script. Checking for update.
Checked out revision 625452.

# 3/11 - Saving uninstall commands for your current revision.
No current revision was found.

# 4/11 - Checking out common SVN files.
Checked out revision 625452.

# 5/11 - Updating Amarok files.
At revision 625452.

# 6/11 - Getting localization and documentation:
- # Checking out default (American English) documentation.
Checked out revision 625452.

# 7/11 - Preparing for configuration. (This will take a while.)
This Makefile is only for the CVS repository
This will be deleted before making the distribution

/home/m0rph/amarok-svn/unsermake/unsermake -f admin/Makefile.common cvs
./admin/cvs.sh: line 33: --version: command not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
Error creating cvs. Exit status 1.
Error creating all. Exit status 1.

ERROR: Preparation failed.
Problems at this step are quite certainly problems with either unsermake or your automake configuration.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-m0rph"
Link points to "/tmp/kde-m0rph"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

m0rph@m0rph:~$ ./amarok-svn.sh 
Amarok-svn (Version 3.1.1)
============================

Used configuration
--------------------
(Use --help to get information on how to change it.)

SVN server:                                     svn://anonsvn.kde.org
Language for localization and documentation:    en_US
Extra configuration options:                    --with-libmtp
Command for getting root privileges:            kdesu
Build ID:                                       Off
Build directory:                                /home/m0rph/amarok-svn
Clean source tree:                              Off

###################### #### ### ## ## ## # #

# 1/11 - Checking out base files.
Checked out revision 625452.

# 2/11 - Getting unsermake.
Unsermake downloaded by this script. Checking for update.
Checked out revision 625452.

# 3/11 - Saving uninstall commands for your current revision.
No current revision was found.

# 4/11 - Checking out common SVN files.
Checked out revision 625452.

# 5/11 - Updating Amarok files.
At revision 625452.

# 6/11 - Getting localization and documentation:
- # Checking out default (American English) documentation.
Checked out revision 625452.

# 7/11 - Preparing for configuration. (This will take a while.)
This Makefile is only for the CVS repository
This will be deleted before making the distribution

/home/m0rph/amarok-svn/unsermake/unsermake -f admin/Makefile.common cvs
./admin/cvs.sh: line 33: --version: command not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
Error creating cvs. Exit status 1.
Error creating all. Exit status 1.

ERROR: Preparation failed.
Problems at this step are quite certainly problems with either unsermake or your automake configuration.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-m0rph"
Link points to "/tmp/kde-m0rph"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


m0rph@m0rph:~$ ./amarok-svn.sh 
Amarok-svn (Version 3.1.1)
============================

Used configuration
--------------------
(Use --help to get information on how to change it.)

SVN server:                                     svn://anonsvn.kde.org
Language for localization and documentation:    en_US
Extra configuration options:                    --with-libmtp
Command for getting root privileges:            kdesu
Build ID:                                       Off
Build directory:                                /home/m0rph/amarok-svn
Clean source tree:                              Off

###################### #### ### ## ## ## # #

# 1/11 - Checking out base files.
Checked out revision 625452.

# 2/11 - Getting unsermake.
Unsermake downloaded by this script. Checking for update.
Checked out revision 625452.

# 3/11 - Saving uninstall commands for your current revision.
No current revision was found.

# 4/11 - Checking out common SVN files.
Checked out revision 625452.

# 5/11 - Updating Amarok files.
At revision 625452.

# 6/11 - Getting localization and documentation:
- # Checking out default (American English) documentation.
Checked out revision 625452.

# 7/11 - Preparing for configuration. (This will take a while.)
This Makefile is only for the CVS repository
This will be deleted before making the distribution

/home/m0rph/amarok-svn/unsermake/unsermake -f admin/Makefile.common cvs
./admin/cvs.sh: line 33: --version: command not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
Error creating cvs. Exit status 1.
Error creating all. Exit status 1.

ERROR: Preparation failed.
Problems at this step are quite certainly problems with either unsermake or your automake configuration.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-m0rph"
Link points to "/tmp/kde-m0rph"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

###############ONSCREEN ERROR##################
Preparation failed.
Problems at this step are quite certainly problems with either unsermake or your automake configuration.
#############################################

I AWAIT YOUR REPLY on how to proceed...

P.S.
I must also add that my system is now running even smoother and faster after running the
sudo apt-get install kdebase kdebase-dev gxine libxine-dev ruby ruby1.8-dev python python2.4-dev

Sometimes i would assume this is a by product of running packages but i'm now back 
to stage 1 where i would like to now get Amarok to work. with my CVM.... :D 



I AWAIT YOUR REPLY on how to proceed...

---

### Post by riven0 on 2007-01-20
I'm a little late on this thread... but is there any reason why your trying to manually compile Amarok instead of installing it through apt-get? It would be easier if you let apt take care of it.

---

### Post by NESFreak on 2007-01-20
> **riven0 said:**
> I'm a little late on this thread... but is there any reason why your trying to manually compile Amarok instead of installing it through apt-get? It would be easier if you let apt take care of it.

amarok from apt-get doesn't supports libmtp. basically it's missing tree files. So you need to install libmtp from synaptic. install amarok from synaptic. and unzip this archive in your root.
[http://www.ubuntuforums.org/showthread.php?t=273137](http://www.ubuntuforums.org/showthread.php?t=273137)

It's easy, and way more diskspace friendly.

NESFreak

---

### Post by schwascore on 2007-01-20
You could try that package in the post above if you would like.  I like using the amarok-svn script because it lets you compile the latest and greatest from the amarok svn repository and you can re-compile it with support for different features. Every month I run the script again and it will only download and compile what it needs to update your amarok version to the latest svn version.  But that's just me and my preference.

Anyways, if you're still interested in using the script, to fix the autoconf dependency, run this:

```

sudo apt-get install autoconf automake1.8

```

Also, if Xine still doesn't work (it will show up as an error when running the script), you can try the following:
```
sudo apt-get install xine-ui
```

or you can get it  here: [http://prdownloads.sourceforge.net/xine/xine-lib-1.1.3.tar.gz](http://prdownloads.sourceforge.net/xine/xine-lib-1.1.3.tar.gz) and install it with checkinstall much like libmtp and libnjb as you did with the gnomad2 install.  Your choice, both should work just fine.

FYI: You're almost done with the install if you choose to continue with the script.

---

### Post by m0rph on 2007-01-20
After following all of your instructions schwascore, I now get;

========================
 ===  Amarok - ERROR  ==========================================================
 ========================
 =
 = Amarok cannot be built because, either the TagLib library is not installed,
 = or if relevant, the taglib-devel package is not installed.
 = TagLib can be obtained from: [http://ktown.kde.org/~wheeler/taglib/](http://ktown.kde.org/~wheeler/taglib/)
 =
 ==================================
 ===  AMAROK WILL NOT BE BUILT  ================================================
 ==================================
 =
 = Some mandatory dependencies are either not installed or not installed
 = correctly. See the Amarok README for help with this issue. Further assistance
 = can be found at [http://amarok.kde.org](http://amarok.kde.org) or in amarok on irc.freenode.net.
 = You will still be able to build other modules from extragear/multimedia.
 =
 ===============================================================================

ERROR: Configuration failed. Amarok was NOT installed/upgraded.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I like the sound of running this script to keep Amarok up to date each Month so I would like to get it to work before I try NESFreak help of installing libmtp from synaptic......

I await your reply........ ):P

---

### Post by m0rph on 2007-01-21
Ok so I downloaded & compiled TagLib library that was missing
ran ./amarok-svn.sh
got an error around step 11 of the above script
I have now removed all traces of Amarok off my machine and ran
./amarok-svn.sh

the following is where I'm at now;

checking for xmllint... /usr/bin/xmllint
checking for Qt docs... NO
checking for dot... not found
checking for doxygen... not found
checking for pkg-config... yes
checking for taglib-config... /usr/local/bin/taglib-config
checking for xine-config... yes
checking for xine-lib version >= 1.0.2... yes
checking for stdint.h... (cached) yes
checking whether fabsf is declared... yes
checking linux/inotify.h usability... yes
checking linux/inotify.h presence... yes
checking for linux/inotify.h... yes
checking for Qt with OpenGL support... yes
checking for int... (cached) yes
checking size of int... (cached) 4
checking for short... (cached) yes
checking size of short... (cached) 2
checking for long... (cached) yes
checking size of long... (cached) 4
checking for char *... (cached) yes
checking size of char *... (cached) 4
checking for sdl-config... no
checking tunepimp-0.5/tp_c.h usability... no
checking tunepimp-0.5/tp_c.h presence... no
checking for tunepimp-0.5/tp_c.h... no
checking tunepimp/tp_c.h usability... no
checking tunepimp/tp_c.h presence... no
checking for tunepimp/tp_c.h... no
checking if sched_setaffinity should be enabled... yes
checking konqsidebarplugin.h usability... yes
checking konqsidebarplugin.h presence... yes
checking for konqsidebarplugin.h... yes
checking for _init in -lkonqsidebarplugin... yes
checking for pkg-config... /usr/bin/pkg-config
checking for libnjb... yes
checking LIBNJB_CFLAGS...
checking LIBNJB_LIBS... -lnjb -lusb
checking for libmtp >= 0.1.1... yes
checking LIBMTP_CFLAGS...
checking LIBMTP_LIBS... -lmtp -lusb
checking libkarma/lkarma.h usability... no
checking libkarma/lkarma.h presence... no
checking for libkarma/lkarma.h... no
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes

checking ifp.h usability... no
checking ifp.h presence... no
checking for ifp.h... no
checking for usb.h... (cached) yes

checking for libgpod-1.0... checking for statvfs... yes
checking if KDE is at least 3.4 for DAAP support... yes
checking for uint8_t... yes
checking for u_int8_t... yes
checking for uint16_t... yes
checking for u_int16_t... yes
checking for uint32_t... yes
checking for u_int32_t... yes
checking for uint64_t... yes
checking for u_int64_t... yes
checking for ruby... /usr/bin/ruby
checking ruby.h usability... yes
checking ruby.h presence... yes
checking for ruby.h... yes
checking if amarok should be compiled... yes
checking if doc should be compiled... yes
configure: creating ./config.status
fast creating Makefile
fast creating amarok/Makefile
fast creating amarok/src/Makefile
fast creating amarok/src/amarokcore/Makefile
fast creating amarok/src/analyzers/Makefile
fast creating amarok/src/collectionscanner/Makefile
fast creating amarok/src/data/Makefile
fast creating amarok/src/device/Makefile
fast creating amarok/src/device/massstorage/Makefile
fast creating amarok/src/device/nfs/Makefile
fast creating amarok/src/device/smb/Makefile
fast creating amarok/src/engine/Makefile
fast creating amarok/src/engine/akode/Makefile
fast creating amarok/src/engine/gst10/Makefile
fast creating amarok/src/engine/gst10/config/Makefile
fast creating amarok/src/engine/gst10/equalizer/Makefile
fast creating amarok/src/engine/helix/Makefile
fast creating amarok/src/engine/helix/config/Makefile
fast creating amarok/src/engine/helix/helix-sp/Makefile
fast creating amarok/src/engine/kdemm/Makefile
fast creating amarok/src/engine/mas/Makefile
fast creating amarok/src/engine/nmm/Makefile
fast creating amarok/src/engine/nmm/icons/Makefile
fast creating amarok/src/engine/void/Makefile
fast creating amarok/src/engine/xine/Makefile
fast creating amarok/src/engine/yauap/Makefile
fast creating amarok/src/images/Makefile
fast creating amarok/src/images/icons/Makefile
fast creating amarok/src/konquisidebar/Makefile
fast creating amarok/src/loader/Makefile
fast creating amarok/src/magnatunebrowser/Makefile
fast creating amarok/src/mediadevice/Makefile
fast creating amarok/src/mediadevice/daap/Makefile
fast creating amarok/src/mediadevice/daap/daapreader/Makefile
fast creating amarok/src/mediadevice/daap/daapreader/authentication/Makefile
fast creating amarok/src/mediadevice/daap/mongrel/Makefile
fast creating amarok/src/mediadevice/daap/mongrel/http11/Makefile
fast creating amarok/src/mediadevice/daap/mongrel/lib/Makefile
fast creating amarok/src/mediadevice/daap/mongrel/lib/mongrel/Makefile
fast creating amarok/src/mediadevice/daap/mongrel/lib/rbconfig/Makefile
fast creating amarok/src/mediadevice/daap/mongrel/lib/rubygems/Makefile
fast creating amarok/src/mediadevice/generic/Makefile
fast creating amarok/src/mediadevice/ifp/Makefile
fast creating amarok/src/mediadevice/ipod/Makefile
fast creating amarok/src/mediadevice/mtp/Makefile
fast creating amarok/src/mediadevice/njb/Makefile
fast creating amarok/src/mediadevice/riokarma/Makefile
fast creating amarok/src/metadata/Makefile
fast creating amarok/src/metadata/aac/Makefile
fast creating amarok/src/metadata/audible/Makefile
fast creating amarok/src/metadata/m4a/Makefile
fast creating amarok/src/metadata/mp4/Makefile
fast creating amarok/src/metadata/rmff/Makefile
fast creating amarok/src/metadata/speex/Makefile
fast creating amarok/src/metadata/trueaudio/Makefile
fast creating amarok/src/metadata/wav/Makefile
fast creating amarok/src/metadata/wavpack/Makefile
fast creating amarok/src/metadata/wma/Makefile
fast creating amarok/src/plugin/Makefile
fast creating amarok/src/scripts/Makefile
fast creating amarok/src/scripts/common/Makefile
fast creating amarok/src/scripts/graphequalizer/Makefile
fast creating amarok/src/scripts/lyrics_astraweb/Makefile
fast creating amarok/src/scripts/lyrics_lyrc/Makefile
fast creating amarok/src/scripts/playlist2html/Makefile
fast creating amarok/src/scripts/ruby_debug/Makefile
fast creating amarok/src/scripts/score_default/Makefile
fast creating amarok/src/scripts/score_impulsive/Makefile
fast creating amarok/src/scripts/templates/Makefile
fast creating amarok/src/scripts/webcontrol/Makefile
fast creating amarok/src/sqlite/Makefile
fast creating amarok/src/statusbar/Makefile
fast creating amarok/src/themes/Makefile
fast creating amarok/src/themes/example/Makefile
fast creating amarok/src/themes/reinhardt/Makefile
fast creating amarok/src/themes/reinhardt/images/Makefile
fast creating amarok/src/vis/Makefile
fast creating amarok/src/vis/libvisual/Makefile
fast creating doc/Makefile
fast creating doc/en/Makefile
config.pl: fast created 80 file(s).
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

 ==========================
 ===  Amarok - PLUGINS  ======================================================== ==========================
 =
 = The following extra functionality will NOT be included:
 =   - NMM-engine
 =   - Helix-engine
 =   - yauap-engine
 =   - libvisual Support
 =   - MySql Support
 =   - Postgresql Support
 =   - MusicBrainz Support
 =   - MP4/AAC Tag Write Support
 =   - iPod Support
 =   - iRiver iFP Support
 =   - Rio Karma Support
 =
 = The following extra functionality will be included:
 =   + xine-engine
 =   + Konqueror Sidebar
 =   + Creative Nomad Jukebox Support
 =   + MTP Device Support
 =
 ===============================================================================
Good - your configure finished. Start make now


# 9/11 - Compiling. (The time of this step depends on the number of new source files that were downloaded.)

Compilation successful after 0 minute(s) and 4 second(s).

# 10/11 - Comparing uninstall commands.
Differences in the uninstall commands were found, uninstalling your current revision.
Executing 'kdesu' to get root privileges for uninstallation.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
uninstalling /home/m0rph/amarok-svn/amarok/src/amarok_proxy.rb
uninstalling ./amarok/src/amarokapp
uninstalling /home/m0rph/amarok-svn/amarok/src/amarokitpc.protocol
uninstalling /home/m0rph/amarok-svn/amarok/src/amaroklastfm.protocol
uninstalling /home/m0rph/amarok-svn/amarok/src/amarokpcast.protocol
uninstalling /home/m0rph/amarok-svn/amarok/src/amarok_addaspodcast.desktop
uninstalling /home/m0rph/amarok-svn/amarok/src/amarok_append.desktop
uninstalling /home/m0rph/amarok-svn/amarok/src/amarok_play_audiocd.desktop
uninstalling /home/m0rph/amarok-svn/amarok/src/amarok.profile.xml
uninstalling ./amarok/src/libamarok.la
uninstalling /home/m0rph/amarok-svn/amarok/src/amarokrc
uninstalling /home/m0rph/amarok-svn/amarok/src/amarok_plugin.desktop
uninstalling /home/m0rph/amarok-svn/amarok/src/amarok_codecinstall.desktop
uninstalling /home/m0rph/amarok-svn/amarok/src/amarokui.rc
uninstalling /home/m0rph/amarok-svn/amarok/src/amarok.desktop
uninstalling /home/m0rph/amarok-svn/amarok/src/amarokcore/amarok.kcfg
uninstalling /home/m0rph/amarok-svn/amarok/src/data/Cool-Streams.xml
uninstalling /home/m0rph/amarok-svn/amarok/src/data/Amarok_1.4_Welcome.ogg
uninstalling /home/m0rph/amarok-svn/amarok/src/data/ball.png
uninstalling /home/m0rph/amarok-svn/amarok/src/data/dot.png
uninstalling /home/m0rph/amarok-svn/amarok/src/data/equalizer_presets.xml
uninstalling /home/m0rph/amarok-svn/amarok/src/data/firstrun.m3u
uninstalling /home/m0rph/amarok-svn/amarok/src/data/grid.png
uninstalling /home/m0rph/amarok-svn/amarok/src/data/wirl1.png
uninstalling /home/m0rph/amarok-svn/amarok/src/data/wirl2.png
uninstalling /home/m0rph/amarok-svn/amarok/src/data/magnatune_start_page.html
uninstalling /home/m0rph/amarok-svn/amarok/src/data/magnatune_logo.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/amarok_cut.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/amarok_rocks.jpg
uninstalling /home/m0rph/amarok-svn/amarok/src/images/b_next.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/b_pause.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/b_play.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/b_prev.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/b_stop.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/back_stars_grey.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/currenttrack_bar_left.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/currenttrack_bar_mid.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/currenttrack_bar_right.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/currenttrack_play.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/currenttrack_pause.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/currenttrack_stop.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/currenttrack_stop_small.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/currenttrack_repeat.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/currenttrack_repeat_small.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/eq_active2.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/eq_inactive2.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/lastfm.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/loading1.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/loading2.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/menu_sidepixmap.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/more_albums.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/musicbrainz.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/nocover.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/pl_active2.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/pl_inactive2.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/shadow_albumcover.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/sbinner_stars.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/smallstar.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/splash_screen.jpg
uninstalling /home/m0rph/amarok-svn/amarok/src/images/star.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/time_minus.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/time_plus.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/vol_speaker.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/volumeslider-gradient.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/volumeslider-handle.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/volumeslider-handle_glow.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/volumeslider-inset.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/wizard_compact.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/wizard_xmms.png
uninstalling /home/m0rph/amarok-svn/amarok/src/images/xine_logo.png
uninstalling ./amarok/src/loader/amarok
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/common/Zeroconf.py
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/common/Publisher.py
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/lyrics_astraweb/COPYING
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/lyrics_astraweb/README
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/lyrics_astraweb/lyrics_astraweb.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/lyrics_astraweb/lyrics_astraweb.spec
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/lyrics_lyrc/COPYING
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/lyrics_lyrc/README
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/lyrics_lyrc/lyrics_lyrc.spec
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/lyrics_lyrc/lyrics_lyrc.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/playlist2html/Playlist.py
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/playlist2html/README
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/playlist2html/playlist2html.py
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/playlist2html/PlaylistServer.py
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/ruby_debug/debug.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/score_default/score_default.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/score_default/COPYING
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/score_default/README
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/score_default/score_default.spec
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/score_impulsive/COPYING
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/score_impulsive/README
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/score_impulsive/score_impulsive.spec
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/score_impulsive/score_impulsive.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/templates/python_qt_template.py
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/templates/ruby_qt_template.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/templates/amarok.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/Globals.py
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/Playlist.py
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/README
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/RequestHandler.py
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/WebControl.spec
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/WebPublisher.py
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/amarok_cut.png
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/controlbackground.png
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/main.css
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/main.js
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/player_end.png
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/player_pause.png
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/player_play.png
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/player_start.png
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/player_stop.png
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/template.thtml
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/vol_speaker.png
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/star.png
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/smallstar.png
uninstalling /home/m0rph/amarok-svn/amarok/src/scripts/webcontrol/WebControl.py
uninstalling /home/m0rph/amarok-svn/amarok/src/themes/example/stylesheet.css
uninstalling /home/m0rph/amarok-svn/amarok/src/themes/reinhardt/stylesheet.css
uninstalling /home/m0rph/amarok-svn/amarok/src/themes/reinhardt/images/background.png
uninstalling /home/m0rph/amarok-svn/amarok/src/themes/reinhardt/images/transparency.png
uninstalling /home/m0rph/amarok-svn/amarok/src/konquisidebar/amarok.desktop
uninstalling /home/m0rph/amarok-svn/amarok/src/konquisidebar/amarok.desktop
uninstalling ./amarok/src/konquisidebar/konqsidebar_universalamarok.la
uninstalling /home/m0rph/amarok-svn/amarok/src/konquisidebar/amarok.desktop
uninstalling /home/m0rph/amarok-svn/amarok/src/engine/void/amarok_void-engine_plugin.desktop
uninstalling ./amarok/src/engine/void/libamarok_void-engine_plugin.la
uninstalling /home/m0rph/amarok-svn/amarok/src/engine/xine/amarok_xine-engine.desktop
uninstalling /home/m0rph/amarok-svn/amarok/src/engine/xine/xinecfg.kcfg
uninstalling ./amarok/src/engine/xine/libamarok_xine-engine.la
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/generic/amarok_generic-mediadevice.desktop
uninstalling ./amarok/src/mediadevice/generic/libamarok_generic-mediadevice.la
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/amarok_daap-mediadevice.desktop
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/amarok_daapserver.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/codes.rb
uninstalling ./amarok/src/mediadevice/daap/libamarok_daap-mediadevice.la
uninstalling ./amarok/src/mediadevice/daap/mongrel/http11/libhttp11.la
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/http11/http11.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/gem_plugin.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/gemconfigure.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/mongrel.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/mongrel/cgi.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/mongrel/command.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/mongrel/configurator.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/mongrel/debug.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/mongrel/handlers.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/mongrel/init.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/mongrel/stats.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/mongrel/tcphack.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/._gem_commands.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/builder.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/cmd_manager.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/command.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/config_file.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/custom_require.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/dependency_list.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/doc_manager.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/format.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/gem_commands.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/gem_openssl.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/gem_runner.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/incremental_fetcher.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/installer.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/loadpath_manager.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/old_format.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/open-uri.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/package.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/remote_installer.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/rubygems_version.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/security.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/source_index.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/specification.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/timer.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/user_interaction.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/validator.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rubygems/version.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/daap/mongrel/lib/rbconfig/datadir.rb
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/njb/amarok_njb-mediadevice.desktop
uninstalling ./amarok/src/mediadevice/njb/libamarok_njb-mediadevice.la
uninstalling /home/m0rph/amarok-svn/amarok/src/mediadevice/mtp/amarok_mtp-mediadevice.desktop
uninstalling ./amarok/src/mediadevice/mtp/libamarok_mtp-mediadevice.la
uninstalling /home/m0rph/amarok-svn/amarok/src/device/massstorage/amarok_massstorage-device.desktop
uninstalling ./amarok/src/device/massstorage/libamarok_massstorage-device.la
uninstalling /home/m0rph/amarok-svn/amarok/src/device/nfs/amarok_nfs-device.desktop
uninstalling ./amarok/src/device/nfs/libamarok_nfs-device.la
uninstalling /home/m0rph/amarok-svn/amarok/src/device/smb/amarok_smb-device.desktop
uninstalling ./amarok/src/device/smb/libamarok_smb-device.la
uninstalling ./amarok/src/collectionscanner/amarokcollectionscanner

# 11/11 - Installing files.
Executing 'kdesu' to get root privileges for installation.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Terminal now hangs at Failed to open device
Your advise would be appreciated........ ](*,)

---

### Post by m0rph on 2007-01-21
Well after rebooting and starting again from scratch i was able to get the 
Amarok-svn Script to run and install Amarok 1.4

Ok now thats over with, i quickly went into it and followed schwascore Steps 7,8 9.

With the unhappy result of
No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window.

Am I surprised, yes, i thought once this worked all would be ok...

well at least after following schwascore

sudo apt-get install kdebase kdebase-dev gxine libxine-dev ruby ruby1.8-dev python python2.4-dev

my system is running very fast 
ie; faster boot and shutdown, faster webpapes and flipping between tabs in firefox.....

I am now prepared to follow your advise NESFreak but cannnot understand the link you posted, would you be so kind as to advise what the steps would be......

Thankyou again schwascore for all of your advise but i still cannot get my CZVM to work ](*,)

---

### Post by m0rph on 2007-01-21
Hey schwascore,

After double checking everything on the gnomad2 guide i noticed your post at the end of the guide and relised the following (See my post);

[http://ubuntuforums.org/showthread.php?t=199250&page=40](http://ubuntuforums.org/showthread.php?t=199250&page=40)

I can now get my CZVM to work with Gnomad2, Yaaaaaa.......

If only now i could get it to work with Amarok :biggrin: 

To repeat my above post words;
I am now prepared to follow your advise NESFreak but cannnot understand the link you posted, would you be so kind as to advise what the steps would be......
and schwascore anywmore tips to get Amarok to work with NESFreak way of things...

---

### Post by NESFreak on 2007-01-21
> **m0rph said:**
> Hey schwascore,

After double checking everything on the gnomad2 guide i noticed your post at the end of the guide and relised the following (See my post);

[http://ubuntuforums.org/showthread.php?t=199250&page=40](http://ubuntuforums.org/showthread.php?t=199250&page=40)

I can now get my CZVM to work with Gnomad2, Yaaaaaa.......

If only now i could get it to work with Amarok :biggrin: 

To repeat my above post words;
I am now prepared to follow your advise NESFreak but cannnot understand the link you posted, would you be so kind as to advise what the steps would be......
and schwascore anywmore tips to get Amarok to work with NESFreak way of things...

download [this archive]("http://ubuntuforums.org/attachment.php?attachmentid=23375&d=1169145323") and save it in your homedir (don't use "save as"). now you should open the commandline (, go to your homedir if your not already in it or if you did save it on another directory cd to wherever you put it) and enter this command```
sudo unzip amarok_mtp.zip -d /
```
Now start up amarok go to settings, configure amarok, media devices, (auto detect won't work in gnome), add device, chose MTP media device as your plugin, give it some random name, and DON'T give it a mount point. get rid of the settings screen (OK), click on mediadevice in the sidebar, select your just added mediadevice and press connect.
this should do the trick.

NESFreak

---

### Post by m0rph on 2007-01-22
Hey NESFreak,

Tried the above but when in Amarok the only devices i can choose is;

Do not handle
Generic Audio Player
Music Sharing
Creative Nomad Juke Box Media Device

If i select the last one then try to connect on the mediadevice in the sidebar
still no connection ?
It does call it a NJB Media Device on the mediadevice in the sidebar

Any thoughts......... ????

---

### Post by NESFreak on 2007-01-22
> **m0rph said:**
> Hey NESFreak,

Tried the above but when in Amarok the only devices i can choose is;

Do not handle
Generic Audio Player
Music Sharing
Creative Nomad Juke Box Media Device

If i select the last one then try to connect on the mediadevice in the sidebar
still no connection ?
It does call it a NJB Media Device on the mediadevice in the sidebar

Any thoughts......... ????

thats because NJB is an older protocol used by creative before they switched to mtp.

These files are from amarok 1.4.4 and since you have compiled it yourself i think your version just isn't compatible with these files. You could try uninstalling your version and then reinstalling from the repros. Though the  "--with-mtp" flag you added while compiling should have created these files for you. See if you can find the following files somewhere where you have compiled amarok.
libamarok_mtp-mediadevice.so
libamarok_mtp-mediadevice.la
amarok_mtp-mediadevice.desktop

and copy them to
/usr/lib/kde3/libamarok_mtp-mediadevice.so
/usr/lib/kde3/libamarok_mtp-mediadevice.la
/usr/share/services/amarok_mtp-mediadevice.desktop

if you cant find them anywhere something must have gone wrong while compiling.

BTW i suppose gnomad2 does work for you.
NESFreak

---

### Post by m0rph on 2007-01-23
Hey NESFreak,
> 
You could try uninstalling your version and then reinstalling from the repros. 

What command can i type in the terminal todo this so I can then choose Amarok from 
within the repros..... 

These files seem tobe where they should be so this is my last resort.

---

### Post by NESFreak on 2007-01-23
> **m0rph said:**
> Hey NESFreak,


What command can i type in the terminal todo this so I can then choose Amarok from 
within the repros..... 

These files seem tobe where they should be so this is my last resort.

go to the build directory and enter "make uninstall"

and since you're using dapper i'd recommend downloading the amarok package from the official amarok site. [http://amarok.kde.org/wiki/Download:Kubuntu](http://amarok.kde.org/wiki/Download:Kubuntu).

NESFreak

btw try installing the edgy version first, if it complains about libs, try the dapper version.

---

### Post by m0rph on 2007-01-25
Having trouble uninstalling this Amarok Script refered to by schwascore
Whenever i type "make uninstall" the following response comes up

make: *** No rule to make target `uninstall'.  Stop.

Please advise how i can remove this script that schwascore has recomended 
earlier on page 1 of this thread.......

What directory is the build directory ? :mad:

---

### Post by undertakingyou on 2007-01-27
The build folder I believe is the amarok-svn folder in your home directory.  It doesn't seem to have a way to uninstall the newly built amarok.   Also, NESFreak's zipped files _WILL NOT_ work with the svn-built amarok.  I don't know why but they just don't.  The way that I got it to work with NESFreak's files is I had a totally fresh install (I actually reinstalled the OS, but if you can find a way to uninstall the compiled amarok you wouldn't have to, it may require actually deleting the directories that the packages and build create).  Before you install amarok install the libusb and libmtp packages using synaptic, then make sure you have the 1.4.4 amarok package available in synaptic and install that and anything that it needs.  After that, and before running amarok for the first time, I unzipped NESFreak's files.  Then I ran amarok and aula!! success!!  I must thank NESFreak for having those files.  I think that is great.  I hope this helped.  That's how I got it to work. :D

UNDERTAKING YOU--
------------------------

---

### Post by m0rph on 2007-01-27
Cheers:biggrin: :biggrin:

---

### Post by Kougaiji on 2007-02-21
Alright I got my Amarok nice and working with my Vision: M!

Yay! I just started using Ubuntu, my first linux os, about a week ago!

So now I have one slight other problem with the issue at hand, and it's probably because of MTP, but Amarok won't let me play files nor copy them off my Vision: M. I can see them all just fine, though. Do I need an additional plugin or did I miss something?

---

### Post by Markmiran on 2007-05-20
Wouldn't it be better for everyone if we could just automount the silly thing, and then use the file explorer to drag and drop our music into the Zen folders.  I can do this is windows, but linux no??? Such a simple thing - yet I can't do it here.  Frankly speaking both Gnomad 2 and Amarok suck!!!! I have always prefered to drag and drop into the the file explorer... Does anyone out there have a solution thats better than running these two packages?

Thanks guys...

---

