---
title: "Bad screen recording"
date: 2012-08-04
forum: Any Other OS
---

### Post by Halbblutplins on 2012-08-04
I tried to record my desktop ffmpeg but i get so bad results, it seems i recorded with only 5fps but i recorded with 30fps. I also get with kazam, eidete, recordmydesktop and xvidcap so bad results. :( With ffmpeg I also tried many codecs but nothing helped.

ffmpeg code:

```
ffmpeg -f x11grab -s hd1080 -i :0.0 -r 30 -qscale 1 -vcodec mpeg4 /home/*****/testvid.mp4
```Hope someone can help me!

My system specs:
- AMD Phenom(tm) II X4 3Ghz
- Geforce GTX 550ti by Club3D
- 8GB DDR3
- Mint 13
- video driver 295.49

---

### Post by Perfect Storm on 2012-08-04
Moved to Other OS/Distro Talk.

---

### Post by Sarcastic Cows on 2012-08-05
Hmm... they're some pretty decent specs...

Are you trying to record a game or something? If it's a programme using a lot of memory, you may get bad results

Does your video card work properly as well

I'm not sure whether in Mint you can set specific tasks to specific cores, if your processor is multi-core, which, by the looks of it, probably is.

---

### Post by FakeOutdoorsman on 2012-08-06
> **Halbblutplins said:**
> I tried to record my desktop ffmpeg but i get so bad results, it seems i recorded with only 5fps but i recorded with 30fps.

Try a faster encoder: [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719)

---

### Post by Halbblutplins on 2012-08-11
> **Sarcastic Cows said:**
> Hmm... they're some pretty decent specs...

Are you trying to record a game or something? If it's a programme using a lot of memory, you may get bad results

Does your video card work properly as well

I'm not sure whether in Mint you can set specific tasks to specific cores, if your processor is multi-core, which, by the looks of it, probably is.


Yes, I'm trying to record a game, Minecraft. My videocard is fast  enough, I think (Minecraft 150fps??). I installed Ubuntu 12.04 (my  favorite distro..) but I get same results.
I wanted to post a new thread in the nvidia forums, [LINK]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14"), but I don't have permissions to -.- .

Hope someone can help me.

*Update: Even if I don't record a game i get so bad results.

---

