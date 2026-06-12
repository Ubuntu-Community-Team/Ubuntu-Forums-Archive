---
title: "Ubuntu Codec issues.. HELP!!!!!"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by kenjinn - 320 on 2007-02-13
Hi i am new to ubuntu and i understand quite abit about comand lines. but to the point my linux cant conect to the internet, and i have a doulboot system with ubuntu, and windows xp pro. my in istalation can connet to the net and i can copy files to my ubuntu harddrive and i was wondering if anyone can help me get the files for the Win32codec pack and the libdvdcss2 pack and how to install them that way? any help would be much appritiated.

---

### Post by ashmew2 on 2007-02-13
> **kenjinn - 320 said:**
> Hi i am new to ubuntu and i understand quite abit about comand lines. but to the point my linux cant conect to the internet, and i have a doulboot system with ubuntu, and windows xp pro. my in istalation can connet to the net and i can copy files to my ubuntu harddrive and i was wondering if anyone can help me get the files for the Win32codec pack and the libdvdcss2 pack and how to install them that way? any help would be much appritiated.

Hi , all the files u need to get audio/video files working in UBuntu are these :
gstreamer0.10-pitfdll 
gstreamer0.10-ffmpeg 
gstreamer0.10-plugins-bad
 gstreamer0.10-plugins-bad-multiverse 
gstreamer0.10-plugins-ugly 
gstreamer0.10-plugins-ugly-multiverse 
gxine
 libxine-main1
 libxine-extracodecs
 ogle 
ogle-gui
 
For win32codecs : [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
For libdvdcss2 : [http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0sarge0.0_i386.deb](http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0sarge0.0_i386.deb)
After uve noted down all the package names , goto [packages.ubuntu.com]("packages.ubuntu.com") and click the name of ur Ubuntu distribution and then find the package name u want and save to a CD or ny partition.Ask more if u have ne probs :D

Btw , y isnt ur intrnet working in Ubuntu if its in XP ?

---

### Post by bigken on 2007-02-13
I would get my internet working 1st then you could use [automatix ]("http://www.getautomatix.com/")to install all the sound and video codecs for you

---

### Post by Cueball696 on 2007-02-13
ok I know this is not about your help, but I did not know how to post a new thread.. so I am sorry to be asking here..

but what this mean down where the errors are.. please help? See I am trying to run libdvdcss so I can watch my movies.. but when I type make this is what happen.

cueballnoc@CueballNOC-laptop:~/libdvdcss-1.2.1$ make
Making all in src
make[1]: Entering directory `/home/cueballnoc/libdvdcss-1.2.1/src'
make  all-recursive
make[2]: Entering directory `/home/cueballnoc/libdvdcss-1.2.1/src'
Making all in dvdcss
make[3]: Entering directory `/home/cueballnoc/libdvdcss-1.2.1/src/dvdcss'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/cueballnoc/libdvdcss-1.2.1/src/dvdcss'
make[3]: Entering directory `/home/cueballnoc/libdvdcss-1.2.1/src'
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -DDVDCSS_DIST -g -O2 -c libdvdcss.c
mkdir .libs
gcc -DHAVE_CONFIG_H -I. -I. -I. -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -DDVDCSS_DIST -g -O2 -c libdvdcss.c  -fPIC -DPIC -o .libs/libdvdcss.lo
libdvdcss.c: In function 'dvdcss_read':
libdvdcss.c:407: error: invalid lvalue in assignment
libdvdcss.c:417: error: invalid lvalue in assignment
libdvdcss.c: In function 'dvdcss_readv':
libdvdcss.c:461: error: invalid lvalue in increment
libdvdcss.c:469: error: invalid lvalue in assignment
libdvdcss.c:470: error: invalid lvalue in assignment
make[3]: *** [libdvdcss.lo] Error 1
make[3]: Leaving directory `/home/cueballnoc/libdvdcss-1.2.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/cueballnoc/libdvdcss-1.2.1/src'
make[1]: *** [all-recursive-am] Error 2
make[1]: Leaving directory `/home/cueballnoc/libdvdcss-1.2.1/src'
make: *** [all-recursive] Error 1
cueballnoc@CueballNOC-laptop:~/libdvdcss-1.2.1$

---

### Post by meborc on 2007-02-13
if you build your own stuff you will beed also the **build-essential** package... but it also has a lot of dependancies as it is only a metapackage...

i would try to get the internet to work... it is way more easier then!

---

### Post by Cueball696 on 2007-02-13
> **meborc said:**
> if you build your own stuff you will beed also the **build-essential** package... but it also has a lot of dependancies as it is only a metapackage...

i would try to get the internet to work... it is way more easier then!

o I have every up and running.. but that even able to burn CD.. I just was thinking it was something simple

---

