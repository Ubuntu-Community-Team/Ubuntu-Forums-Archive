---
title: "Sound problem."
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-05-23
I am running Xubuntu dapper/drake testing dual-boot on my Windows machine, I am using onboard Realtek AC97 sound, now my sound card is detected, I've made sure that sound is up using the alsamixer at the command line, and everything is up, however, I can't get any sound out of Totem or Xfmedia (everythings configured to use my soundcard ?) but I can out of XMMS, but only if I put the "PCM" sound up all the way through the mixer, I can't with mpeg videos or any other videos using totem (and there is no way to configure the output?) same with Xfmedia, no sound from mp3's/wav's nor mpeg videos, I add a mp3 to the playlist or something else click play and it just stops immediately, no sound, nothing, how can I fix this? everything runs perfect but the sound ](*,) - and I didn't even notice (I just checked to see if the soundcard was detected) until today when I got around to mounting the drives with my media on it. Anyway to fix this?

---

### Post by Sef on 2006-05-23
Dapper and AC '97 do have some problems, but nothing that can't be fixed.  

First let's check the easy things:

1) Have you downloaded the codecs?

[RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats")

2) Right click the sound icon on the top tool bar > Open Volume Control > Make sure nothing is muted.

3) System > Preferences > Sound  check to make sure the card is the default.

---

### Post by Just4 on 2006-05-23
Ah, problem was with the codecs. Thanks for the help, seems everythings running fine now.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs ffmpeg lame faad sox mjpegtools libxine-main1
```

Fixed everything, or so it seems so far, I'll post back later if I find anymore problems, but so far everything seems good, Xfmedia is working, XMMS is still working, and Totem is working with all of my video files.

---

### Post by Sef on 2006-05-23
You're welcome.   Glad to hear you got sound now.  If you have any questions, please post them here.

---

