---
title: "SanDisk Sansa e250 Tagging"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by neko18 on 2006-12-26
Has anyone had any luck with id3 tagging on the Sansa e250? I've tried editing their tags in Amarok, RhythmBox, and the `id3v2` utility, but no matter what I do the e250 won't organize the tracks by artist/album and simply displays the filename as the song title.

Thanks for any help,
Neko

Edit: I have it set in MSC (aka UMS) mode and I'm dragging my collection (which is composed of MP3s) into the /MUSIC folder on the e250.

---

### Post by organica on 2007-01-27
I'm running into the same issue.  The only thing I can do for this is to Rip with Sound Juicer, re-write the id3v2 tags with EasyTag, then copy over to my sansa using the mass storage device setting.  Can't seem to get the gstreamer-lame to write the id3v2 tags properly.  Yet the sansa may not read properly either.

My mp3 rip setttings are:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=128 ! id3v2mux
```

---

### Post by Zwack on 2007-02-07
From comments I've seen elsewhere there are two versions of id3v2 tags.  Easytag writes the older version that the e2x0{r} series can read.  

I tagged all of my songs with Easytag and it works for me.

If you search for Sansa you will find a beginners guide thread with lots of information.

The one thing that is still missing is video.  

Z.

---

