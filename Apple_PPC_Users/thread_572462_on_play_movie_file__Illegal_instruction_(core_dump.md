---
title: "on play movie file : Illegal instruction (core dumped)"
date: 2007-10-10
forum: Apple PPC Users
---

### Post by erez1012 on 2007-10-10
i upgrade ubuntu to 7.04 and i install mplayer and alll the codec

music is ok but whan i wont to see movie i get this :

erez@IGLD-77-124-65-105:~$ mplayer -vo x11 /home/erez/Desktop/&#1488;&#1489;&#1497;&#1489;&#1492;-&#1488;&#1492;&#1493;&#1489;&#1514;&#1497;-DVIX-&#1495;&#1497;&#1497;&#1501;.[wnet.co.il].aviMPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
AltiVec not found
CPU: PowerPC
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/erez/Desktop/&#1488;&#1489;&#1497;&#1489;&#1492;-&#1488;&#1492;&#1493;&#1489;&#1514;&#1497;-DVIX-&#1495;&#1497;&#1497;&#1501;.[wnet.co.il].avi.
AVI file format detected.
VIDEO: [DX50] 640x340 24bpp 25.000 fps 780.1 kbps (95.2 kbyte/s)
================================================== ========================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
================================================== ========================
================================================== ========================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16be, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
================================================== ========================
AO: [alsa] 44100Hz 2ch s16be (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 340 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.88:1 - prescaling to correct movie aspect.
VO: [x11] 640x340 => 640x340 Planar YV12
Illegal instruction (core dumped)
erez@IGLD-77-124-65-105:~$


everising ok and the screen come up. and suddenly this massage come "Illegal instruction (core dumped)"

i install vlc and other player and it the same problem !!

i book 3g power pc 750 300mhz 256mb

yes it is an old computer but when i install ubuntu 5 mplayer works graet

now with 7.04 it is dont work
__________________

---

### Post by BladeMelbourne on 2007-10-14
I had this issue on an up-to-date Gutsy.

I think a version of mplayer that came down using apt-get/synaptic/etc might have been screwy.

I downloaded and installed:
[http://http.us.debian.org/debian/pool/main/m/mplayer/mplayer_1.0~rc1-16.1_powerpc.deb](http://http.us.debian.org/debian/pool/main/m/mplayer/mplayer_1.0~rc1-16.1_powerpc.deb)
[http://http.us.debian.org/debian/pool/main/m/mplayer-blue/mplayer-skin-blue_1.6-2_all.deb](http://http.us.debian.org/debian/pool/main/m/mplayer-blue/mplayer-skin-blue_1.6-2_all.deb)
(dpkg -i filename1.deb filename2.deb)

I haven't had any (frustrating!) crashes since. I realise you are using 7.04 and I am using 7.10 rc - but it might just work for you.

---

### Post by erez1012 on 2007-10-16
sorry your solution not work for me

---

### Post by andi666 on 2007-10-18
[http://ubuntuforums.org/showthread.php?t=536128](http://ubuntuforums.org/showthread.php?t=536128)

---

