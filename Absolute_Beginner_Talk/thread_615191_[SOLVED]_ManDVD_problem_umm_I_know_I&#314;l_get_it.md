---
title: "[SOLVED] ManDVD problem umm I know I&#314;l get it eventually"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by hogwartsnigel on 2007-11-16
Hi All you wonderful Ubuntu users....thanks for even looking at this thread.

I have Mandvd and like the look of its interface greatly and it promises to do all I need but I get this error when I try and make a slideshow...can anyone in simple terms step me through how to correct the problem.

[I][dvd-slideshow] Creating ac3 audio for /home/nigel/Music/Podcasts/triple j_ WE LOVE AUSMUSIC/institut_polaire.mp3...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/nigel/Videos/New man/dvd-slideshow.log for details
[dvd-slideshow] cleanup...[/I]

I have posted this elsewhere but the guy helping cut off, probably annoyed at my failure to understand the posted amendment to dvd-slideshow, anyway if you could please keep it simple.

Thanks

:)Nigel

---

### Post by disturbedite on 2007-11-16
could you actually post the contents of */home/nigel/Videos/New man/dvd-slideshow.log?*

---

### Post by hogwartsnigel on 2007-11-16
Yes I will tonight my time......I am on another pc right now...please subscribe and I&#314;l post later today with full log...

Thanks for noticing (god I sound like eeyore from winnie the poooh...BAH!)

Nigel

---

### Post by hogwartsnigel on 2007-11-17
Dear Disturbedite,
Not sure how to pull the mandvd log....i reattempted a simple slideshow and the attempt to generate the same error..
as before...it appears to be the ffmpeg componant unable to process ac3..the last attempt to help me went down the lines of correcting dvd-slideshow into using ac2 (I have no idea what that means but sounded good to write as if I did..lol)
Can you help either how to alter dvd-slideshow or get the mandvd logfiles.

Thanks

Greatly appreciated

Nigel

---

### Post by hogwartsnigel on 2007-11-17
Cool I found it...der should have followed your directions to my own file...always trying to use a GUI..tut tut.


here is the log contents

[I][dvd-slideshow] Sat Nov 17 16:45:19 EST 2007
[dvd-slideshow] Command line was:
[dvd-slideshow] /usr/bin/dvd-slideshow -o /home/nigel/Videos/New man/ -n slideshow_16:45:19 -p -L -f slideshow.txt -a /home/nigel/Music/omen.mp3
[dvd-slideshow] dvd-slideshow version 0.7.5
[dvd-slideshow] Linux nigel-ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
[dvd-slideshow] Output directory=/home/nigel/Videos/New man
[dvd-slideshow] Using /bin/bash version GNU bash, version 3.2.25(1)-release (i486-pc-linux-gnu)
[dvd-slideshow] Found mjpegtools version 1.8.0
[dvd-slideshow] Using mjpegtools subsampling -S 420mpeg2
[dvd-slideshow] Found sox version Version
[dvd-slideshow] Found ImageMagick version 6.2.4
[dvd-slideshow] Found dvdauthor version 0.6.14.
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896
[dvd-slideshow] Font=-font /usr/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] ####################################
[dvd-slideshow] Parsing input .txt file slideshow.txt
[dvd-slideshow]############################################################
[dvd-slideshow] Found 81 images.
[dvd-slideshow] Found 1 audio files.
[dvd-slideshow] Found 0 background slides.
[dvd-slideshow] Found 0 title slides.
[dvd-slideshow] Found 6 transitions (fadein/fadeout/crossfade).
[dvd-slideshow] Video: PAL  Audio: AC3
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=render
[dvd-slideshow] WARNING: Using low-quality mode.
[dvd-slideshow]   This mode is for testing only.
[dvd-slideshow]   output resolution is x
[dvd-slideshow]   Ignore [mpeg2enc] warnings (usually)
[dvd-slideshow] Decoding command-line passed audio files...
[dvd-slideshow] Decoding mp3 audio: /home/nigel/Music/omen.mp3
[dvd-slideshow] Total video length = 0:3:41.500
[dvd-slideshow] Temp dir is /home/nigel/Videos/New man/dvd-slideshow_temp_9114
COMMAND        PID  USER   FD   TYPE DEVICE SIZE     NODE NAME
dvd-slideshow 9114 nigel    3w  FIFO    3,4      15597783 /home/nigel/Videos/New man/dvd-slideshow_temp_9114/dvdss-pipe-9114
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] 1/81 transition0_0.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 2/81 transition0_1.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 3/81 transition0_2.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 4/81 transition0_3.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 5/81 transition0_4.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 6/81 transition0_5.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 7/81 transition0_6.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 8/81 transition0_7.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 9/81 transition0_8.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 10/81 transition0_9.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 11/81 transition0_10.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 12/81 transition0_11.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 13/81 transition0_12.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 14/81 transition0_13.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 15/81 transition0_14.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:0.500
[dvd-slideshow]############################################################
[dvd-slideshow] 16/81 gibusima_x0.jpg 0:0:33.000
[dvd-slideshow]############################################################
[dvd-slideshow] 17/81 transition1_0.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 18/81 transition1_1.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 19/81 transition1_2.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 20/81 transition1_3.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 21/81 transition1_4.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 22/81 transition1_5.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 23/81 transition1_6.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 24/81 transition1_7.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 25/81 transition1_8.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 26/81 transition1_9.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 27/81 transition1_10.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 28/81 transition1_11.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 29/81 transition1_12.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 30/81 transition1_13.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 31/81 transition1_14.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:0.500
[dvd-slideshow]############################################################
[dvd-slideshow] 32/81 gibusima_x1.jpg 0:0:33.000
[dvd-slideshow]############################################################
[dvd-slideshow] 33/81 transition2_0.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 34/81 transition2_1.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 35/81 transition2_2.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 36/81 transition2_3.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 37/81 transition2_4.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 38/81 transition2_5.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 39/81 transition2_6.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 40/81 transition2_7.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 41/81 transition2_8.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 42/81 transition2_9.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 43/81 transition2_10.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 44/81 transition2_11.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 45/81 transition2_12.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 46/81 transition2_13.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 47/81 transition2_14.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:0.500
[dvd-slideshow]############################################################
[dvd-slideshow] 48/81 gibusima_x2.jpg 0:0:33.000
[dvd-slideshow]############################################################
[dvd-slideshow] 49/81 transition3_0.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 50/81 transition3_1.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 51/81 transition3_2.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 52/81 transition3_3.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 53/81 transition3_4.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 54/81 transition3_5.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 55/81 transition3_6.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 56/81 transition3_7.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 57/81 transition3_8.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 58/81 transition3_9.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 59/81 transition3_10.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 60/81 transition3_11.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 61/81 transition3_12.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 62/81 transition3_13.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 63/81 transition3_14.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:0.500
[dvd-slideshow]############################################################
[dvd-slideshow] 64/81 gibusima_x3.jpg 0:0:33.000
[dvd-slideshow]############################################################
[dvd-slideshow] 65/81 transition4_0.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 66/81 transition4_1.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 67/81 transition4_2.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 68/81 transition4_3.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 69/81 transition4_4.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 70/81 transition4_5.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 71/81 transition4_6.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 72/81 transition4_7.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 73/81 transition4_8.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 74/81 transition4_9.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 75/81 transition4_10.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 76/81 transition4_11.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 77/81 transition4_12.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 78/81 transition4_13.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] 79/81 transition4_14.jpg 0:0:0.200
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:0.500
[dvd-slideshow]############################################################
[dvd-slideshow] 80/81 gibusima_x4.jpg 0:0:33.000
[dvd-slideshow]############################################################
[dvd-slideshow] 81/81 gibusima_x5.jpg 0:0:37.000
[dvd-slideshow]############################################################
[dvd-slideshow] Fadeout 0:0:2.000
[dvd-slideshow]############################################################
[dvd-slideshow] mpeg2enc process=17968
[dvd-slideshow] output from ps=  PID TTY      STAT   TIME COMMAND
17968 ?        S      0:32 mpeg2enc -v 0 -a 2 -q 4 -4 2 -2 1 -s -M 0 -f 8 -o /home/nigel/Videos/New man/dvd-slideshow_temp_9114/video_0.mpg
COMMAND         PID  USER   FD   TYPE DEVICE     SIZE     NODE NAME
dvd-slideshow  9114 nigel    3w  FIFO    3,4          15597783 /home/nigel/Videos/New man/dvd-slideshow_temp_9114/dvdss-pipe-9114
mpeg2enc      17968 nigel    3w   REG    3,4 16400384 15597786 /home/nigel/Videos/New man/dvd-slideshow_temp_9114/video_0.mpg
[dvd-slideshow] waiting for mpeg2enc to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] Processing command-line audio...
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] /home/nigel/Music/omen.mp3
[dvd-slideshow] fade_in_time=0:0:3.000 fade_out_time=0:0:3.000
[dvd-slideshow] total_audio_length=0:3:43.688
[dvd-slideshow] ###############
[dvd-slideshow] Creating ac3 audio for /home/nigel/Music/omen.mp3...
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, wav, from '/home/nigel/Videos/New man/dvd-slideshow_temp_9114/audio1.wav':
  Duration: 00:03:41.6, start: 0.000000, bitrate: 1536 kb/s
  Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Output #0, ac3, to '/home/nigel/Videos/New man/dvd-slideshow_temp_9114/audio1.ac3':
  Stream #0.0: Audio: ac3, 48000 Hz, 5:1, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/nigel/Videos/New man/dvd-slideshow.log for details
[dvd-slideshow] cleanup...[/I]

Hope that can help. On first look to the extreme novice it points to....um (I sit here clueless the sound file was a 128 MP3 and the screen FPS was 5 if that helps

Nigel

---

### Post by hogwartsnigel on 2007-11-17
Ok the problem isn't with mandvd as i get this using qdvd author 
an ac3 error too. so it is something to with this.

HELP

---

### Post by disturbedite on 2007-11-17
here is the output of my ffmpeg --formats
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --libdir=${prefix}/lib --shlibdir=${prefix}/lib --incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir=${prefix}/share/man --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-pp --enable-libamr-nb --enable-libamr-wb --enable-x11grab --enable-libogg --enable-libgsm --enable-libx264 ***--enable-liba52*** --enable-libtheora --extra-cflags=-Wall -g -fPIC -DPIC --cc=ccache cc --enable-swscaler

looks like you're missing a bunch of those including liba52 which is the ac3 codec.

btw, you're attempting to encode a stereo wav file to 5.1 surround, you know that won't actually "enhance" the sound right?  it can't work magic and make it sound like its natively 5.1 surround cuz the original source file was only stereo.  it won't hurt, but it doesn't actually make it sound better, per se.

---

### Post by hogwartsnigel on 2007-11-17
Thanks,
Yeh I know that I can't enhance the sound....I think I've just set it as a default.

Thanks for your support...i have ffmpeg enabled so I guess i simply ensure all the libs are extracted from the repositary..correct...hope so.

Thanks again. I'll write back after I've attempted to find and install them.

ta 

again

Nigel

---

### Post by hogwartsnigel on 2007-11-17
Hi I ensure all the lib inc lib52 was installed ran man dvd and tried to generate lideshow got the same message

[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] /home/nigel/Music/omen.mp3
[dvd-slideshow] fade_in_time=0:0:3.000 fade_out_time=0:0:3.000
[dvd-slideshow] total_audio_length=0:3:43.688
[dvd-slideshow] ###############
[dvd-slideshow] Buffering end of audio file with silence for 0:1:27.872
[dvd-slideshow] Creating ac3 audio for /home/nigel/Music/omen.mp3...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/nigel/Videos/New man/dvd-slideshow.log for details
[dvd-slideshow] cleanup...

The log states truncated to the end of...

[dvd-slideshow] 607/608 transition37_14.jpg 0:0:0.048
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:0.500
[dvd-slideshow]############################################################
[dvd-slideshow] 608/608 gibusima_x37.jpg 0:0:7.000
[dvd-slideshow]############################################################
[dvd-slideshow] Fadeout 0:0:2.000
[dvd-slideshow]############################################################
[dvd-slideshow] mpeg2enc process=8375
[dvd-slideshow] output from ps=  PID TTY      STAT   TIME COMMAND
 8375 ?        S      0:52 mpeg2enc -v 0 -a 2 -q 4 -4 2 -2 1 -s -M 0 -f 8 -o /home/nigel/Videos/New man/dvd-slideshow_temp_7855/video_0.mpg
COMMAND        PID  USER   FD   TYPE DEVICE     SIZE     NODE NAME
dvd-slideshow 7855 nigel    3w  FIFO    3,4          15564807 /home/nigel/Videos/New man/dvd-slideshow_temp_7855/dvdss-pipe-7855
mpeg2enc      8375 nigel    3w   REG    3,4 33656832 15564810 /home/nigel/Videos/New man/dvd-slideshow_temp_7855/video_0.mpg
[dvd-slideshow] waiting for mpeg2enc to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] Processing command-line audio...
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] /home/nigel/Music/omen.mp3
[dvd-slideshow] fade_in_time=0:0:3.000 fade_out_time=0:0:3.000
[dvd-slideshow] total_audio_length=0:3:43.688
[dvd-slideshow] ###############
[dvd-slideshow] Buffering end of audio file with silence for 0:1:27.872
[dvd-slideshow] Creating ac3 audio for /home/nigel/Music/omen.mp3...
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, wav, from '/home/nigel/Videos/New man/dvd-slideshow_temp_7855/audio1.wav':
  Duration: 00:05:10.5, start: 0.000000, bitrate: 1536 kb/s
  Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Output #0, ac3, to '/home/nigel/Videos/New man/dvd-slideshow_temp_7855/audio1.ac3':
  Stream #0.0: Audio: ac3, 48000 Hz, 5:1, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/nigel/Videos/New man/dvd-slideshow.log for details
[dvd-slideshow] cleanup...

Do I need to completely uninstall and start again or am I missing something

Thanks for your patience...I keep reading my own title for this thread to ensure my patience.

Nigel

---

### Post by RJQ on 2007-11-27
Look at this page, the fella called Galicia 360 has the answer, and yes this is the kind of answer that I do not know from where  in the whole hearth this  people get them, any way work wonders for me, now there is no problem in any ffmpeg execution, I am currently using ubuntu gutsy hope it helps.

[http://wwww.kde-apps.org/content/show.php?content=14129&PHPSESSID=34c62d7f79a718672a3345e2e51810b7](http://wwww.kde-apps.org/content/show.php?content=14129&PHPSESSID=34c62d7f79a718672a3345e2e51810b7)


I think his adress for the .deb file is wrong, any way just type ffmpeg in the search box once you get to the Debian packages page.

---

### Post by hogwartsnigel on 2007-11-27
Thanks RJQ,
I sorted with the help os some friends by amending the dvd-slideshow source...turns out was an update error. had to amend 3 x 192 entries to 192K such a little thing but it worked for me..
Anyway thanks for your input. I'll change this to solved.

Ta

---

