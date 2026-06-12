---
title: "Do you use Mplayer? If so, can you help me?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-09-13
Hello Ubuntu Users & Greetings!

Until recently I was watching some live media streams from a couple of websites using mplayer. Everything was working until I changed some settings. When working correctly the video and audio were set as:

video output = x11
audio output = oss


BUT THEN..... I messed with the "minium Cache Size and Percent of Media to cache settings and now the audio is out of sync with the videio. I.E. audio plays faster than video.....

Could someone using Mplayer tell me the values for the following:

Minimum Cache size ??????????????
Percent of media to cache ?????????

When your video setting is set on x11 and oss for audio.....

To find the values you simply right click on a playing video stream and choose configure at the bottom of the list.

Thanks for helping me.....

---

### Post by eduardounder on 2007-09-13
Try to delete the configs.. (You are going to lose all your config)

You can do that using the terminal:
> 
rm -rf .mplayer


---

### Post by Maestro23 on 2007-09-13
Mine are 512 & 25.

---

### Post by lentomies on 2007-09-13
I don't want to delete my settings at this time. First I want to use the two value settings I requested.

---

### Post by lentomies on 2007-09-13
Maestro23 Thanks for the info.... was your audio and video set to x11 and oss?

---

### Post by Maestro23 on 2007-09-13
> **lentomies said:**
> Maestro23 Thanks for the info.... was your audio and video set to x11 and oss?

Just double-checked:  Video is x11 & Audio is alsa.

Well, might put you on the right path anyway.  Good luck.

---

