---
title: "mplayer wierd acting"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-12-14
here goes a strange one. mplayer GUI won't work when started from Multimedia->Mplayer. it gives me a "fatal error" when i try to open a file to play...any file (and i mean video files)! but if i go to mc and press enter on a video file everything works fine! any clue of why this happens? how do i fix this?:confused:

---

### Post by taurus on 2006-12-14
What happens if you start it from a terminal?

```
gmplayer filename.avi
```

---

### Post by mendingo84 on 2006-12-14
same error. this is the output:
> 
Playing /media/hda5/movie/Something_new/smth.avi.
AVI file format detected.
VIDEO:  [XVID]  496x368  12bpp  23.976 fps  837.6 kbps (102.2 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
SUB: Detected subtitle file format: subviewer
SUB: Read 1414 subtitles.
SUB: Adjusted 1 subtitle(s).
SUB: Added subtitle file (1): /media/hda5/movie/Something_new/Something New.srt
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.4 kbit/8.36% (ratio: 16049->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)


---

### Post by taurus on 2006-12-14
It is having a problem with an audio output.  Start it from a terminal and go into Preferences -> Audio and change to another audio driver...

```
gmplayer
```

---

### Post by mendingo84 on 2006-12-14
that won't do :(...i tried it

---

### Post by taurus on 2006-12-14
That would do meaning you still get the same error message!  How did you install mplayer anyway?

---

### Post by mendingo84 on 2006-12-14
intstalled it using adept manager

---

### Post by taurus on 2006-12-14
Do you have any problem playing that video file with another media player like vlc?

---

### Post by mendingo84 on 2006-12-14
i can play those files using the Kaffeine GUI for example

---

### Post by taurus on 2006-12-14
Okay, run gmplayer from a terminal again and follow this...

Applications -> Sound & Video -> MPlayer Movie Player -> Preferences -> Codecs & demux. Make sure both "Video codec family" & "Audio codec family" are using the "FFmpeg's libavcodec codec family" & "FFmpeg/libavcodec audio decoders", respectively.

Then restart.

---

### Post by mendingo84 on 2006-12-15
nope...not even that way :(...this is annoying! it's not me, i can run mplayer from the konsole, but my girlfriend is also using this notebook and she is just a user, that's why i am so keen on fixing this!

---

### Post by akamaleldin on 2006-12-29
Try:
MPlayer --> Preferences --> Video Tab and Choose xv
Hope it works ...

---

