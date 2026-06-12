---
title: "Idiot-proof way to extract the audio from a FLV file (youtube file)"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-07-14
Title says it al. Most of it. I can't handle obscure references to script files, and have to fill in the blanks myself...that usually results in some random error.

---

### Post by Acglaphotis on 2007-07-14
real simple, just do a

```
mplayer -dumpaudio videohere.flv -dumpfile nameofoutput.mp3
```

---

### Post by FleetAdmiral74 on 2007-07-15
Worked like a charm, thanks. Is there a simply way to change the output format, to say ogg?

---

### Post by Malice007 on 2007-09-07
Did not work for me????

malice@dell:~$ mplayer -dumpaudio MyHumps.flv -dumpfile Myhumps.mp3
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing MyHumps.flv.
File not found: 'MyHumps.flv'
Failed to open MyHumps.flv.


Exiting... (End of file)

---

### Post by Malice007 on 2007-09-07
MMm I got all the errors and just figured it did not work. When I closed Firefox and looked on my desktop there was the mp3. Don't know why I get all the errors but it works :)

---

### Post by steveking on 2008-06-10
YouTubeRobot.com today announces YouTube Robot 2.0, a tool that enables you to download video from YouTube.com onto your PC, convert it to various formats to watch it when you are on the road on mobile devices like mobile phone, iPod, iPhone, Pocket PC, PSP, or Zune.

YouTube Robot allows you to search for videos using keywords or browse video by category, author, channel, language, tags, etc. When you find something noteworthy, you can preview the video right in YouTube Robot and then download it onto the hard disk drive. The speed, at which you will be downloading, is very high: up to 5 times faster than other software when you download a single file and up to 4 times faster when you download multiple files at a time.

Manual download is not the only option with YouTube Robot. You may as well schedule the download and conversion tasks to be executed automatically, even when you are not around. Downloading is followed by conversion to the format of your choice and uploading videos to a mobile device (if needed). For example, you can plug in iPod, select the video, go to bed, and when you wake up next morning, your iPod will be ready to play new YouTube videos.

Product page: [www.youtuberobot.com](www.youtuberobot.com)
Direct download link: [www.youtuberobot.com/download/utuberobot.exe](www.youtuberobot.com/download/utuberobot.exe)
Company web-site: [www.youtuberobot.com](www.youtuberobot.com)

---

### Post by Gademis on 2008-07-17
[http://maketecheasier.com/ubuntu-how-to-extract-audio-from-youtube-video/2008/06/30](http://maketecheasier.com/ubuntu-how-to-extract-audio-from-youtube-video/2008/06/30)

Haven't check it yet...

---

