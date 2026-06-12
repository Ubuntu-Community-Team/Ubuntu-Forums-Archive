---
title: "Having trouble playing MP3 files"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by IbanezShredder on 2008-02-01
I just want to be able to play my damn music. I open up the music player, it tells me I need to install the GStreamer extra codecs so I can play mp3 files. It wont let me install it, it says other software is conflicting it from installing and I need to remove it.... one problem though.... it doesn't tell me what to remove so i'm stuck. Please help me out here.

---

### Post by barrack on 2008-02-01
I'm assuming that you read this article:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

If you were anything like me, you only followed the directions for 7.10 or 7.04.

I found that the 6.10 commands were helpful too. Basically you need to install the good bad and ugly gstreamer stuff. You can look for them in synaptic, or run this code.

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

Hope that helps.

---

### Post by IbanezShredder on 2008-02-01
when I type the sudo code it asks me for my password but i cant type it in, it's like the keyboars isnt functioning at all lol wtf, this happens everytime I type a sudo code

---

### Post by kernel tom on 2008-02-01
the cursor will not move when you enter ur password for sudo, trust its working

---

### Post by kalia_n on 2008-02-03
thanks barrack
it's working

---

