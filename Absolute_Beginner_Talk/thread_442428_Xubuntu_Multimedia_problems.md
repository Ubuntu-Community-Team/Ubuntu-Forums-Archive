---
title: "Xubuntu Multimedia problems"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by NovaNine on 2007-05-13
Hi again.
I was wondering, I entered this code to update my multimedia capabilities :

```
sudo apt-get install libxine-extracodecs ffmpeg lame faad sox mjpegtools gxineplugin flashplugin-nonfree
```

But then the terminal tells me this : E: Couldn't find package libxine-extracodecs

What's wrong ? :confused:

---

### Post by ugm6hr on 2007-05-13
Not sure.  But I installed the extracodecs from the GUI:
1. Make sure you are connected to the internet.
2a. Applications -> System -> Add/Remove...
2b. Click "Preferences" and make sure there are ticks in all the boxes except "Source Code" (Ubuntu software tab), then close preferences.
3.  Select "Multimedia" (left menu)
4. Scroll down to "Xine extra plugins" (tick box)
5. Click "OK"
That worked for me - Acer Aspire 5051 AWXMi with Xubuntu 7.04 (Feisty).

---

