---
title: "choppy video"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by uthturn on 2008-04-04
Ok so my .mkv and .avi play choppy with ubuntu i have tried some solutions but can't fix it. I have a nvidia 7600 with the restricted drivers i remember trying 1 solution with gstreamer changing it to ugly pack ( i think) but that didn't help. These video play fine under windows the .mkv are much  larger (4gb) and play fine in windows but neither the .avi videos are .mkv play well in ubuntu they are watchable but the video is "choppy" kinda seems like when the screen switches are something thanks for any help

---

### Post by Gen2ly on 2008-04-04
possibly a gstreamer problem??  You could try mplayer which I believe uses xine.

---

### Post by uthturn on 2008-04-04
it seems to be better  butthere is still clipping thanks for the help

---

### Post by Tomatz on 2008-04-04
How do they play in vlc?

If you don't have vlc:

**sudo apt-get install vlc**

---

### Post by uthturn on 2008-04-04
vlc is my main player i've tried gxine and mplayer both about the same i'm not even sure if it is that much better then what i was getting in vlc

---

### Post by Tomatz on 2008-04-04
If your using compiz try changing the video output to X11 in the vlc settings (just check the advanced box in settings to access)

---

### Post by uthturn on 2008-04-04
that made it worse :( thanks anyhow
by worse i mean the video stuttered a little

---

### Post by Tomatz on 2008-04-04
Crud :(

---

### Post by uthturn on 2008-04-04
no harm
thanks for the try:)

---

### Post by uthturn on 2008-04-05
bump i would still like some other ideas if possible:)

---

### Post by Tomatz on 2008-04-05
Do you have the "video playback" plugin in compiz enabled?

---

### Post by gorf 99 on 2008-04-05
For mkv I usually like to use Kaffine but plays well for me in Movie Player.

Make sure that you have all your codecs in, ffmpeg, libdvdread3, libdvdcss2 and very important w32 codecs that you will have to download.

How this helps

---

### Post by Gen2ly on 2008-04-05
any choppyiness in flash or say playing a video game?

---

### Post by uthturn on 2008-04-11
yeah man Flash video (youtube) clips are choppy as well

---

