---
title: "Subtitle trouble with video"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by daou on 2006-08-23
I'm having trouble opening an .avi file and getting subtitles (.sub file, with .idx file) to show up.
I've tried the totem-player, doesn't work.
Xine-ui doesn't work.
Mplayer doesn't work, period. When trying to start mplayer, all I get in the command line is:

```
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Newcastle,Winchester,San Diego,Venice; Sempron Palermo (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Option Creating needs a parameter at line 1
```

and nothing happens, mplayer never shows up.

EDIT: mplayer used to work, haven't used it for a while and don't know what happened.

---

### Post by 505 on 2006-08-23
I don't know about the other players, but you can get subtitles in Totem only if the filename of the sub is the same as the filename of the avi (with .avi replaced by .sub or .srt). If the subtitles are named any different, it's difficult to get them working.

---

### Post by daou on 2006-08-24
The subtitles have the same names as the avi files. Totem freezes when opening an avi file with a sub file in the same directory. Xine controls sometimes freeze when opening subtitles.

I'll try reinstalling libxine and see if that helps.

---

### Post by daou on 2006-08-24
It appears the subtitles were all vobsubs. Normal sub and srt files work.

---

