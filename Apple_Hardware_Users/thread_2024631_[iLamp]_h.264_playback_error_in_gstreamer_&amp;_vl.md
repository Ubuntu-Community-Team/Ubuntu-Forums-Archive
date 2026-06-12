---
title: "[iLamp] h.264 playback error in gstreamer &amp; vlc"
date: 2012-07-13
forum: Apple Hardware Users
---

### Post by wingnut2292 on 2012-07-13
Sorry to complain folks, but I've inherited a 17" USB-1 g4 iLamp, and it's worked great but I seem unable to play h.264 mkv video - I always get the following error: "could not find gstramer caps for ffmpg codec h.264".  mp4 video get's the same error. I don't have any mpeg2 video, ogg-vorbits or webm to try. Xvid seems to work.

As a workaround, WinFF hangs in mid-launch and Lubuntu has to force-kill it, so down-converting video seems out of the question at the moment.  Flash seems EoL'ed. Even if I can get the html5 version of youtube to work, a lot of other sites complain that I need to upgrade to another version of flash, both in Midori and Firefox.

There wouldn't happen to be a MacOS or iOS cousin to WINE, by chance, so that I could extract PPC MacOS h.264 codecs and have that be that?

---

### Post by gwjvan on 2012-07-15
The last poster on this thread said to "Try mplayer2 with smplayer in the repos."

[http://ubuntuforums.org/showthread.php?t=1947544](http://ubuntuforums.org/showthread.php?t=1947544)

There is no response after that, but the thread is marked as solved. Maybe give that a shot

---

### Post by wingnut2292 on 2012-07-16
I did and playback improved. It's a step in the right dirction, as I'd only get video with a black screen and forzen-subtitles if I paused playback before. But now the audio and video are very out of sync. Video playback is noticable slower, too. Perhaps because CPU useage is at 100% as soon as playback sarts?

---

