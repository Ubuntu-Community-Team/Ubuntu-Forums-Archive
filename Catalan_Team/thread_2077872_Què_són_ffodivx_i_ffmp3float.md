---
title: "Què són ffodivx i ffmp3float?"
date: 2012-10-29
forum: Catalan Team
---

### Post by jinglada on 2012-10-29
Tinc un dvd sony i solament reprodueix vídeos divx amb audio mp3.

He descarregat el vídeo [http://www.homenatgeacatalunyaii.org/](http://www.homenatgeacatalunyaii.org/) **-que aprofito per recomenar a tots els usuaris de programari lliure-** i he vist que tenia un format estrany per a mi; el del vídeo és 'ffodivx' i el d'audio és 'ffmp3float'

> **Què són ffodivx i ffmp3float?** Són codecs lliures? He cercat al google i no ho he sabut trobar.

 He intentat convertir el vídeo a 'divx' amb el mencoder i amb el winff i m'ha donat molts errors , com ara això;

amb el mencoder:

```
joan@joan-laptop:~$ mencoder HomenatgeacatalunyaII-catcat832.avi -oac pcm -ovc lavc -lavcopts vcodec=xvid:mbd=2:trell:autoaspect -o histocat2.avi
```

dóna aquest error:

> MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
success: format: 0  data: 0x0 - 0x2a270ccc
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x352  12bpp  25.000 fps  1363.7 kbps (166.5 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:640x352  fps:25.000  ftime:=0.0400
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
AUDIO: 44100 Hz, 2 ch, floatle, 128.0 kbit/4.54% (ratio: 16000->352800)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
Cannot find codec 'xvid' in libavcodec...
Couldn't open video filter 'lavc'.
Failed to open the encoder.

Exiting...
joan@joan-laptop:~$ 

amb el winff quan donava aquesta línia d'ordres:

```
ffmpeg -y -i "HomenatgeacatalunyaII-catcat832.avi" -r 29.97 -vcodec libxvid -vtag XVID -s 640x480 -aspect 4:3 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv -trellis -aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2 -sameq -vtag DIVX "o_HomenatgeacatalunyaII-catcat832.avi"
```

sortia aquest error:

> [libxvid @ 0x7b5c20] [Eval @ 0x7fff2f6c8e60] Invalid chars 'v' at the end of expression '4mv'
[libxvid @ 0x7b5c20] Unable to parse option value "4mv"
[libxvid @ 0x7b5c20] Error setting option flags to value +4mv.

ffmpeg informa que el fitxer és vídeo mpeg4 i àudio mp3

> [avi @ 0x11b29c0] non-interleaved AVI
Input #0, avi, from '/media/572d462a-94a7-41b4-924d-80b6183dbf8e/HomenatgeacatalunyaII-catcat832.avi':
  Duration: 01:02:48.04, start: 0.000000, bitrate: 1501 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 640x352 [PAR 1:1 DAR 20:11], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s
[buffer @ 0x11b9060] w:640 h:352 pixfmt:yuv420p

quan el winff -amb els paràmetres: "converteix a" AVI, "configuracions" 'MS compatible AVI', donava aquesta línia d'ordres:

```
ffmpeg -y -i "HomenatgeacatalunyaII-catcat832.avi" -f avi -acodec libmp3lame -vcodec msmpeg4 -ab 192 -sameq o_HomenatgeacatalunyaII-catcat832.avi"
```

no donava  error però va obtenir un fitxer amb el mateix format amb més del doble de volum i no compatible amb el dvd sony.

A títol informatiu surt el següent text:

> ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use **avconv** instead.

El mplayer identify dóna això:

> joan@joan-laptop:~$ mplayer -identify HomenatgeacatalunyaII-catcat832.avi
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing HomenatgeacatalunyaII-catcat832.avi.
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x352  12bpp  25.000 fps  1363.7 kbps (166.5 kbyte/s)
Load subtitles in 
ID_FILENAME=HomenatgeacatalunyaII-catcat832.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=1363744
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=352
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_START_TIME=0.00
ID_LENGTH=3768.04
ID_SEEKABLE=1
ID_CHAPTERS=0
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Could not grab port 143.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, floatle, 128.0 kbit/4.54% (ratio: 16000->352800)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=ffmp3float

Edito:

Se m'ha acudit provar el vídeo original tal qual l'he descarregat i en el dvd sony funciona!  :(

---

