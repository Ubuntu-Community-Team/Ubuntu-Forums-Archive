---
title: "burning CDs from M4As &amp; MP3s"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2007-11-20
I tried burning a CD in K3B (KB3?) and it doesn't seem to allow any file format other than WAV.

I imagine that there's a plugin and a "sudo" somewhere that will let me use AAC and MP3 files.  Can anyone advise?

(somehow serpentine lets me do this "right out of the box" - that's a much simpler program, obviously, with fewer features.)

Next - does anyone know how I can generate a text file from an .m3u playlist - as in amarok or serpentine or K3B?

thanks!

willfriedwald

---

### Post by skyjacker on 2007-11-22
To handle mp3 format, you need to install an additional codec set.
```
sudo aptitude install libk3b2-mp3
```

---

