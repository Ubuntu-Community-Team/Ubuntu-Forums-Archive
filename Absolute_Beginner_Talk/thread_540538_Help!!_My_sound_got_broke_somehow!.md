---
title: "Help!! My sound got broke somehow!"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-09-01
I am having major problems with my sound.. It used to work perfectly (up until I compiled a custom version of gnome-volume-manager). After I realized it broke my sound system, i completely removed it and redownloaded gnome-volume-manager from the repos. But my sound issues still linger.

Most .mp3 files play, and some .wav files. A lot of .wav files simply won't play, as well as some DVD's and CDs. I can't figure out why...

I have reinstalled
-Ubuntu Restricted Extras
- Gstreamer Extra Plugins
- GStreamer ffmpeg video plugin
- GStreamer plugins for aac,xvid,mpg2,faad
- Gstreamer Plugins for mms,wavpack,quicktime,musepack
- w32codecs (medibuntu repo)
- libdvdcss2 (medibuntu repo)

Trying to play a .wav file that previously worked with totem and vlc yielded these errors:
```

jondecker76@studio-desktop:~/Desktop$ vlc AYC_Vox.wav
VLC media player 0.8.6 Janus
[00000301] wav demuxer error: unsupported codec (vor1)
[00000385] wav demuxer error: unsupported codec (vor1)
[00000394] wav demuxer error: unsupported codec (vor1)
[00000403] wav demuxer error: unsupported codec (vor1)
[00000412] wav demuxer error: unsupported codec (vor1)
[00000421] wav demuxer error: unsupported codec (vor1)
[00000430] wav demuxer error: unsupported codec (vor1)
[00000439] wav demuxer error: unsupported codec (vor1)
[00000448] wav demuxer error: unsupported codec (vor1)
[00000457] wav demuxer error: unsupported codec (vor1)
[00000466] wav demuxer error: unsupported codec (vor1)
[00000475] wav demuxer error: unsupported codec (vor1)
[00000484] wav demuxer error: unsupported codec (vor1)
[00000493] wav demuxer error: unsupported codec (vor1)
[00000502] wav demuxer error: unsupported codec (vor1)
[00000511] wav demuxer error: unsupported codec (vor1)
[00000520] wav demuxer error: unsupported codec (vor1)
[00000529] wav demuxer error: unsupported codec (vor1)
[00000538] wav demuxer error: unsupported codec (vor1)
[00000547] wav demuxer error: unsupported codec (vor1)
[00000556] wav demuxer error: unsupported codec (vor1)
[00000565] wav demuxer error: unsupported codec (vor1)
[00000574] wav demuxer error: unsupported codec (vor1)
[00000280] main playlist: stopping playback
jondecker76@studio-desktop:~/Desktop$ totem AYC_Vox.wav

(totem:19574): GStreamer-WARNING **: pad wavparse0:src returned caps which are not a real subset of its template caps

(totem:19574): GStreamer-CRITICAL **: gst_caps_get_structure: assertion `index < caps->structs->len' failed

(totem:19574): GStreamer-CRITICAL **: gst_structure_get_name: assertion `structure != NULL' failed

** (totem:19574): CRITICAL **: gst_missing_decoder_message_new: assertion `!gst_caps_is_empty (decode_caps)' failed

(totem:19574): GStreamer-CRITICAL **: gst_element_post_message: assertion `message != NULL' failed
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2182): prepare_output (): /play

jondecker76@studio-desktop:~/Desktop$ 



```


Can anyone help me??  I'm so frustrated that I'm about to do a complete reinstall - but its hard to backup a 60GB home directory :(


thanks

Jon

---

### Post by jondecker76 on 2007-09-01
Doing some more testing - XMMS opens and plays the file just fine

---

### Post by jondecker76 on 2007-09-01
Ok another update. I tried the sound file on another ubuntu machine and it doesn't play there either. Maybe this specific file never did play and I never realized it.

Is there a way to find out which codec I need to play it?? (They are older recordings and samples from my Windows-based studio and I really would like to use them in linux!)

thanks again

Jon

---

