---
title: "Help converting Real Media to IPod compatible format"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by long1929 on 2006-07-10
Hi,

First Post so please bear with me.  I have a 60GB IPod.  I'd like to convert some .rm files to the proper format.  I've installed ffmpeg as instructed here: [https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding).  When I try to process the file I get the following error:

skippy@laptop:~$ ffmpeg -i /media/hda4/Video/MIT_Physics_EM_Lecture1.rm -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 /media/hda4/Video/Lecture1.mov
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
  built on Jul 10 2006 14:58:59, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Input #0, rm, from '/media/hda4/Video/MIT_Physics_EM_Lecture1.rm':
  Duration: 00:47:48.8, start: 0.000000, bitrate: 222 kb/s
  Stream #0.0: Audio: 0x0000, 32 kb/s
  Stream #0.1: Video: rv20, yuv420p, 320x240, 12.00 fps, 187 kb/s
Resampling with input channels greater than 2 unsupported.Can't resample.  Aborting.
Abort at ffmpeg.c:1704
Aborted


This seems to be an audio problem.  I have been able to pull the video off separately.  I used the ffmpeg command line because I haven't installed gtkpod or other programs.  I was waiting to see if I could do this first.

Thanks for any help,
Dave

---

### Post by Kobalt on 2006-07-19
Have you checked this HowTo ? 
[http://www.ubuntuforums.org/showthread.php?t=114946]("http://www.ubuntuforums.org/showthread.php?t=114946")

---

### Post by long1929 on 2006-08-20
I had tried the link Kobalt suggested to no avail.  So I gave up and paid $25 for Winavi program mentioned by gambol.  It seems to work OK but sometimes the file size grows by an order of magnitude...

Thanks,
Dave

---

