---
title: "qdvdauthor errors making slideshow"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-04-28
Hi,
i'm tring to make the slideshow with my holydays' photos but i get some errors. 
Here the log:

[dvd-slideshow] ven apr 28 21:12:50 CEST 2006
[dvd-slideshow] dvd-slideshow version 0.7.2
[dvd-slideshow] Output directory=/tmp/Unnamed/
[dvd-slideshow] Found mjpegtools version 1.8.0
[dvd-slideshow] mjpegtools is >= 1.6.3-rc1
[dvd-slideshow] ####################################
[dvd-slideshow] Parsing input .txt file /tmp/Unnamed//My Slideshow.in
[dvd-slideshow] Found 0 images and 1 audio files.
[dvd-slideshow] Video: PAL  Audio: AC3
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=render
[dvd-slideshow] Decoding command-line passed audio files...
[dvd-slideshow] Decoding mp3 audio: /home/lillux/Desktop/_classic_cartoons/bem.mp3
[dvd-slideshow] Total video length = 0:0:0.0
[dvd-slideshow] Temporary directory is /tmp/Unnamed//dvd-slideshow_temp_9987
[dvd-slideshow] Creating black background
[dvd-slideshow]########################################
[dvd-slideshow] waiting for mpeg2enc to finish...
**ERROR: [mpeg2enc] Could not read YUV4MPEG2 header: system error (failed read/write)!
[dvd-slideshow]###############
[dvd-slideshow] Processing audio...
[dvd-slideshow]###############
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] /home/lillux/Desktop/_classic_cartoons/bem.mp3
[dvd-slideshow] fade_in_time=0:0:3.0 fade_out_time=0:0:3.0
[dvd-slideshow] total_audio_length=0:0:0.0
[dvd-slideshow] ###############
[dvd-slideshow] Creating ac3 audio...
FFmpeg version CVS, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --prefix=/usr --libdir=${prefix}/lib --incdir=${prefix}/include/ffmpeg --enable-shared --enable-mp3lame --enable-gpl --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts --enable-amr_nb --enable-amr_wb --enable-pp --enable-libogg --enable-a52 --enable-theora --enable-libgsm --enable-x264 --enable-a52bin 
  libavutil version: 49.0.0
  libavcodec version: 51.7.0
  libavformat version: 50.3.0
  built on Mar 18 2006 07:27:38, gcc: 3.3.5 (Debian 1:3.3.5-13)
Input #0, wav, from '/tmp/Unnamed//dvd-slideshow_temp_9987/audio1.wav':
  Duration: 00:00:00.0, start: 0.000000, bitrate: 1537 kb/s
  Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Output #0, ac3, to '/tmp/Unnamed//dvd-slideshow_temp_9987/audio1.ac3':
  Stream #0.0: Audio: ac3, 48000 Hz, 5:1, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=10000000000.0 bitrate=   0.0kbits/s    

video:0kB audio:0kB global headers:0kB muxing overhead nan%
[dvd-slideshow]########################################
[dvd-slideshow] Multiplexing audio and video...
[dvd-slideshow] Some sequence marker warnings here are normal
**ERROR: [mplex] Unable to open file /tmp/Unnamed//dvd-slideshow_temp_9987/video.mpg for reading.
[dvd-menu] ERROR during mplex execution!
[dvd-menu] see /tmp/Unnamed//dvd-slideshow.log for details

---

### Post by ubunlilluz on 2006-04-29
nobody use qdvdauthor?:(

---

### Post by Sosume on 2006-06-03
I've been having the same errors. I don't know if anybody is still watching this topic, but adding "-S 420mpeg2" to the mpeg2enc command that is used by qdvdauthor fixes the problem.

---

### Post by insulae on 2006-08-29
(first, sorry for my english)

i have a similar error with QDVDAuthor and with ManDVD ( excelent soft: [http://www.kde-apps.org/content/show.php?content=38347](http://www.kde-apps.org/content/show.php?content=38347) ) my problem say, something like: Waiting for mpeg2enc to finish..., y think "meaby is the version of mpeg2enc from ubuntu.
i go try a new version of mpeg2enc. later i tell you if it fix my problem.

---

### Post by insulae on 2006-08-29
Ok i tried to use mjpegtools from edgy, but have a lot unresolved dependencies (i use dapper). so i compiled by my self mjpegtools 1.8.0, and i try to use this "new package" but i have the same error. :mad:

---

### Post by sbassett on 2006-09-26
Try upgrading dvd-slideshow:

[http://sourceforge.net/project/showfiles.php?group_id=100188]("http://sourceforge.net/project/showfiles.php?group_id=100188")

---

### Post by insulae on 2006-09-26
Thanks, my problem is solved.

Regards
insulae

---

