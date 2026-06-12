---
title: "How to capture asf streams on Ubuntu"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by lakersforce on 2007-05-08
Does anyone know how I can capture a asf (windows media) streaming? It does not seem to be possible, but perhaps someone has an answer?

In Denmark, for some reason the national danish tv station DR has decided to run all their streaming content (such as programs and live tv) through microsofts formats. I want to be able to record this on linux.

---

### Post by wthanna on 2007-05-08
There is a program called streamripper.  I'm not sure if it is in the default repositories, but I know it is available using Automatix2.  You can get Automatix2 at  [www.getautomatix.com](www.getautomatix.com)  . You may try using synaptic to download the program first, but I seem to remember using Automatix2, the last time I installed it.  I'm not at one of my Ubuntu machines at the moment or I could verify this for you..  I do know for sure that you can get it using Automatix2, though.

---

### Post by jiminycricket on 2007-05-08
[http://all-streaming-media.com/record-video-stream/record-streaming-video-windows-media-and-real-video.htm](http://all-streaming-media.com/record-video-stream/record-streaming-video-windows-media-and-real-video.htm)

> MPlayer and Related projects (Free/Windows, Linux, Mac OS X,...)
MPlayer is a movie player for Linux (runs on many other Unices, and non-x86 CPUs), Windows, Mac OS X. It plays most MPEG/VOB, AVI, Ogg/OGM, VIVO, ASF/WMA/WMV, QT/MOV/MP4, RealMedia, Matroska, NUT, NuppelVideo, FLI, YUV4MPEG, FILM, RoQ, PVA files, supported by many native, XAnim, and Win32 DLL codecs. You can watch VideoCD, SVCD, DVD, 3ivx, DivX 3/4/5 and even WMV movies, too (without the avifile library).
MPlayer supports streaming via HTTP/FTP, RTP/RTSP, MMS/MMST, MPST, SDP. MPlayer can dump streams (i.e. download them and save to HD). MPlayer supports HTTP, RTSP, MMS protocols to record Windows Media, RealVideo/RealAudio, QuickTime Video
To record streaming media get the URL of a stream and use command line strings like in the following examples:

    mplayer.exe -dumpstream rtsp://somehost.com/somedirectory/somefile.rm
    mplayer.exe -dumpstream rtsp://somehost.com/somedirectory/somefile.ra
    mplayer.exe -dumpstream rtsp://somehost.com/somedirectory/somefile.asf
    mplayer.exe -dumpstream mms://somehost.com/somedirectory/somefile.wmv 

After recording you will get the file stream.dump. You should rename it to .rm, .ra, .asf, .wmv or other format you are using.
Recommended free MPlayer package with GUI for Windows: MPlayer + frontend by Gabor Szecsi (When using it enter your URL in a Media file editbox and "-dumpstream" (without quotes) in MPlayer Extra parameters editbox, then click "Start" button to start recording process

NOt very related to Linux but hopefully it will still work somewhat, replace mplayer.exe with mplayer

---

### Post by livingtarget on 2007-05-08
Yeah the stream dump in mplayer works reasonably well, it's a bit fiddly though with the command line.

---

### Post by lakersforce on 2007-05-08
Nice, I was not aware that mplayer had those capabilities.

But it does not work with the particularly stream I want to download. Looks like I get a "permission denied" if I run with anything other than Windows Mediaplayer. Perhaps there is a work-around?

This is the error message:

```
rune@rune-desktop:~$ mplayer -dumpstream mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR2/2007/04/5bfc245f-ff2f-4013-bdba-d4cf6cfcd538/Tjenesten nu på TV20070413.wmv
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 3200+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR2/2007/04/5bfc245f-ff2f-4013-bdba-d4cf6cfcd538/Tjenesten.
STREAM_ASF, URL: mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR2/2007/04/5bfc245f-ff2f-4013-bdba-d4cf6cfcd538/Tjenesten
Resolving wms.dr.dk for AF_INET6...
Couldn't resolve name for AF_INET6: wms.dr.dk
Resolving wms.dr.dk for AF_INET...
Connecting to server wms.dr.dk[195.85.253.68]: 1755...
Connected
read error:: Operation now in progress
pre-header read failed
Resolving wms.dr.dk for AF_INET6...
Couldn't resolve name for AF_INET6: wms.dr.dk
Resolving wms.dr.dk for AF_INET...
Connecting to server wms.dr.dk[195.85.253.68]: 80...
Server returned 404:Not Found
Failed to parse header.
Failed, exiting.
STREAM_HTTP(2), URL: mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR2/2007/04/5bfc245f-ff2f-4013-bdba-d4cf6cfcd538/Tjenesten
Resolving wms.dr.dk for AF_INET6...
Couldn't resolve name for AF_INET6: wms.dr.dk
Resolving wms.dr.dk for AF_INET...
Connecting to server wms.dr.dk[195.85.253.68]: 80...
Cache size set to 320 KBytes
Stream not seekable!
Core dumped ;)

Exiting... (End of file)
rune@rune-desktop:~$ 

```

---

### Post by lakersforce on 2007-05-08
The "permission denied" section was because of lack of sudo (I think). I ran the command again with sudo and got almost the excact same error message. I am sure that I spelled the url correct.

```
rune@rune-desktop:~$ sudo mplayer -dumpstream mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR2/2007/04/5bfc245f-ff2f-4013-bdba-d4cf6cfcd538/Tjenesten nu på TV20070413.wmv
Password:
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 3200+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR2/2007/04/5bfc245f-ff2f-4013-bdba-d4cf6cfcd538/Tjenesten.
STREAM_ASF, URL: mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR2/2007/04/5bfc245f-ff2f-4013-bdba-d4cf6cfcd538/Tjenesten
Resolving wms.dr.dk for AF_INET6...
Couldn't resolve name for AF_INET6: wms.dr.dk
Resolving wms.dr.dk for AF_INET...
Connecting to server wms.dr.dk[195.85.253.68]: 1755...
Connected
read error:: Operation now in progress
pre-header read failed
Resolving wms.dr.dk for AF_INET6...
Couldn't resolve name for AF_INET6: wms.dr.dk
Resolving wms.dr.dk for AF_INET...
Connecting to server wms.dr.dk[195.85.253.68]: 80...
Server returned 404:Not Found
Failed to parse header.
Failed, exiting.
STREAM_HTTP(2), URL: mms://wms.dr.dk/nas01/auto/cms/Resources/dr.dk/NETTV/DR2/2007/04/5bfc245f-ff2f-4013-bdba-d4cf6cfcd538/Tjenesten
Resolving wms.dr.dk for AF_INET6...
Couldn't resolve name for AF_INET6: wms.dr.dk
Resolving wms.dr.dk for AF_INET...
Connecting to server wms.dr.dk[195.85.253.68]: 80...
Cache size set to 320 KBytes
Stream not seekable!
Core dumped ;)

Exiting... (End of file)
rune@rune-desktop:~$ 
```

---

### Post by Markrian on 2007-05-14
It looks like it worked, actually, there are no problems. In theory, there should be a file called stream.dump in your home directory (or wherever you ran that mplayer command.

That file's the video - rename it as you wish, and mplayer/xine/whatever should be able to play it.

---

### Post by Jose Catre-Vandis on 2007-08-31
It does work, you just have to be patient!

---

### Post by michaelzap on 2007-08-31
Personally I've had better luck with the VLC media player (and it's GUI, too).

---

### Post by Jose Catre-Vandis on 2007-09-02
For some reason I have no joy playing some flv files with vlc or mplayer. i did find this workaround:

[http://www.jeroenwijering.com/?item=Flash_Video_Player](http://www.jeroenwijering.com/?item=Flash_Video_Player)

If you replace the "video.flv" file with your own, naming it "video.flv", then open the html page in firefox, it plays!

---

