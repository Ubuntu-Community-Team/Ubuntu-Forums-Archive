---
title: "ffmpeg install fail"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by natakim on 2007-06-05
arrgh. i've tried four times to install ffmpeg and each time it fails. so far the first and only advise i've had is to try try and try again, done that to no avail. i followed the instructions from here..

[https://wiki.ubuntu.com/ffmpeg?highlight=%28FFMPEG%29]("https://wiki.ubuntu.com/ffmpeg?highlight=%28FFMPEG%29")

and at the end this is my terminal happenings...

> natakim@natakim-desktop:~$ sudo apt-get build-dep ffmpeg
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
natakim@natakim-desktop:~$ sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
liblame-dev is already the newest version.
libfaad2-dev is already the newest version.
libfaac-dev is already the newest version.
libxvidcore4-dev is already the newest version.
liba52-0.7.4 is already the newest version.
liba52-0.7.4-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
natakim@natakim-desktop:~$ apt-get source ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Skipping already downloaded file 'ffmpeg_0.cvs20060823-3.1ubuntu4.dsc'
Skipping already downloaded file 'ffmpeg_0.cvs20060823.orig.tar.gz'
Skipping already downloaded file 'ffmpeg_0.cvs20060823-3.1ubuntu4.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in ffmpeg-0.cvs20060823
natakim@natakim-desktop:~$ cd ffmpeg-*/
[email]natakim@natakim-desktop:~/ffmpeg-0.cvs[/email]20060823$ ./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \
>         --enable-libogg --enable-theora --enable-a52 --enable-dts \
>         --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
>         --enable-faad --enable-faac --enable-xvid
Unknown option "--enable-zlib".
See ./configure --help for available options.
[email]natakim@natakim-desktop:~/ffmpeg-0.cvs[/email]20060823$ make
/home/natakim/ffmpeg-0.cvs20060823/version.sh "/home/natakim/ffmpeg-0.cvs20060823"
make -C libavutil   all
make[1]: Entering directory `/home/natakim/ffmpeg-0.cvs20060823/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/natakim/ffmpeg-0.cvs20060823/libavutil'
make -C libavcodec  all
make[1]: Entering directory `/home/natakim/ffmpeg-0.cvs20060823/libavcodec'
gcc -DHAVE_AV_CONFIG_H -I.. -I/home/natakim/ffmpeg-0.cvs20060823/libavutil -O3  -pthread -Wdeclaration-after-statement -Wall -Wno-switch -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE    -c -o x264.o x264.c
x264.c: In function ‘X264_init’:
x264.c:147: error: ‘struct <anonymous>’ has no member named ‘i_rf_constant’
make[1]: *** [x264.o] Error 1
make[1]: Leaving directory `/home/natakim/ffmpeg-0.cvs20060823/libavcodec'
make: *** [lib] Error 2
[email]natakim@natakim-desktop:~/ffmpeg-0.cvs[/email]20060823$ sudo checkinstall -D make install

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@natakim-desktop ]
1 -  Summary: [ ffmpeg [-i infile] [outfile] ]
2 -  Name:    [ ffmpeg ]
3 -  Version: [ 0.cvs20060823 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ffmpeg-0.cvs20060823 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make -C libavutil   all
make[1]: Entering directory `/home/natakim/ffmpeg-0.cvs20060823/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/natakim/ffmpeg-0.cvs20060823/libavutil'
make -C libavcodec  all
make[1]: Entering directory `/home/natakim/ffmpeg-0.cvs20060823/libavcodec'
gcc -DHAVE_AV_CONFIG_H -I.. -I/home/natakim/ffmpeg-0.cvs20060823/libavutil -O3  -pthread -Wdeclaration-after-statement -Wall -Wno-switch -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE    -c -o x264.o x264.c
x264.c: In function ‘X264_init’:
x264.c:147: error: ‘struct <anonymous>’ has no member named ‘i_rf_constant’
make[1]: *** [x264.o] Error 1
make[1]: Leaving directory `/home/natakim/ffmpeg-0.cvs20060823/libavcodec'
make: *** [lib] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

[email]natakim@natakim-desktop:~/ffmpeg-0.cvs[/email]20060823$ sudo make install
make -C libavutil   all
make[1]: Entering directory `/home/natakim/ffmpeg-0.cvs20060823/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/natakim/ffmpeg-0.cvs20060823/libavutil'
make -C libavcodec  all
make[1]: Entering directory `/home/natakim/ffmpeg-0.cvs20060823/libavcodec'
gcc -DHAVE_AV_CONFIG_H -I.. -I/home/natakim/ffmpeg-0.cvs20060823/libavutil -O3  -pthread -Wdeclaration-after-statement -Wall -Wno-switch -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE    -c -o x264.o x264.c
x264.c: In function ‘X264_init’:
x264.c:147: error: ‘struct <anonymous>’ has no member named ‘i_rf_constant’
make[1]: *** [x264.o] Error 1
make[1]: Leaving directory `/home/natakim/ffmpeg-0.cvs20060823/libavcodec'
make: *** [lib] Error 2
[email]natakim@natakim-desktop:~/ffmpeg-0.cvs[/email]20060823$ y
bash: y: command not found
[email]natakim@natakim-desktop:~/ffmpeg-0.cvs[/email]20060823$ 



any ideas where it is going amiss? 

thanks for your time

---

### Post by Kobalt on 2007-06-05
ffmpeg is available from the Medibuntu repositories. I'd advise you to install it from there. See here how to add these repos : [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by natakim on 2007-06-05
i'll give it a try thanks.

---

### Post by natakim on 2007-06-05
seem to go well but i got this after the last terminal entry..

> natakim@natakim-desktop:~$ sudo apt-get install libdvdcss2 w32codecs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
natakim@natakim-desktop:~$ 


??

---

### Post by aeiah on 2007-06-05
[you can get libdvdcss2 from here](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb) if it isnt in the repos you added (it isnt in the official ubuntu repos for legal reasons but you should have added a repo that it is supposedly in before running your last apt-get command).

for what its worth, it seems your previous problems were related to the x264 codec, although i dont know why it didnt directly list it as a missing dependancy

---

