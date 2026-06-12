---
title: "compressed videos have lagging sound"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-09-13
i've posted threads similar to this one for quite some time now, but have not gotten a response that has fixed my issue.

whenever i'm watching compressed video of any sort..be it youtube, divx, etc...the audio lags on playback. i'm using up to date codecs and drivers, but i can't seem to fix the problem. i've also used the alsa-oss playback method to no avail.

this is my last attempt to get the issue resolved. after this, i'm afraid i'll have to dualboot for video which i feel is unnecessary, but i may be left with no option.

any help is greatly appreciated!!

---

### Post by Shay Stephens on 2006-09-13
I have some videos that were wmv, I converted them to another format, and sound would lag.  I also have some recorded tv shows that are .vob that when converted to ogg or mpeg would lag the sound too.  But these videos lag the sound in windows or linux if I remember right.

The problem I believe is that the video or audio or maybe both have a variable bit rate, and somewhere along the line that is screwing up the timing.

I don't yet have a diagnostic to try or a fix in mind, but it is something I am working on.  Here is what I am currently doing:

Before I start, I have to record the show on DVD of course. Once that is done, I convert it with this:

```
mencoder -dvd-device path_to_dvd dvd://1 -ovc copy -oac pcm -o ripped
```

In my case, the path_to_dvd is /media/cdrom0. Which in turn turns the multiple vob files into one long video file called "ripped"

Then I downsample it and convert to ogg theora video format with this:

```
ffmpeg2theora -v1 -a1 -c1 -x320 -y240 ripped
```


Which generates a 320x240 mono video called ripped.ogg

I have not noticed a sound lag since I started converting this way.  This probably doesn't solve your youtube problems I know.  Probably too simplistic, but what video player are you using?  I know the answer probably is going to be that you have tried all of them :-k

---

### Post by kdoggfunkstah on 2006-09-13
I've been having the same problem as well when I try to watch any youtube videos.  It seems as the lag increases as you watch the video longer. a fix for this would greatly be appreciated!

---

### Post by skymt on 2006-09-13
For Youtube, the problem is in Flash. It'll be fixed in Flash 9.

For other videos, the only time I've seen this is when the video was compressed using a lot of implementation-specific tricks. It's most common in WMV, where the compressor can usually rely on the video only being played back on one player (WMP). Try other players.

---

### Post by shanepardue on 2006-09-13
> **skymt said:**
> For Youtube, the problem is in Flash. It'll be fixed in Flash 9.

For other videos, the only time I've seen this is when the video was compressed using a lot of implementation-specific tricks. It's most common in WMV, where the compressor can usually rely on the video only being played back on one player (WMP). Try other players.
in the compressed video area, i would say it's most common with divx in my case. i've tried switching from vlc, mplayer, and totem. with myplayer, it's a little less noticeable. would tactics like compiling the latest alsa driver be an option or is it more of a codec issue?

---

### Post by shanepardue on 2006-09-13
i take that back. it's a few different codecs besides divx. i installed all my codecs from automatix and that's it. i've installed every codec available for linux. still nothing

---

