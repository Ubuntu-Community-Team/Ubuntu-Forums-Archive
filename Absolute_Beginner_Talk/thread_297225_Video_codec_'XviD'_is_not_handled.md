---
title: "Video codec 'XviD' is not handled"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by EvilAngel on 2006-11-10
Hi all, 

I just installed Edgy on my PC.
I add some packages, adviced on the french Ubuntu planet, in order to handle videos:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
``` 

and I also installed the Mplayer package for Ubuntu.

When I try to open a video using XviD with Totem, I have this message: > Video codec 'XviD' is not handled. You might need to install additional plugins to be able to play some types of movies

Any idea ?

Thanks

---

### Post by CatKiller on 2006-11-10
It's possible that XviD is only included in the gstreamer0.8 plugins. I don't know for sure, though.

Alternatively, you could try playing the film in MPlayer. I know that I have some things that will play in some players, but not in others.

---

### Post by Eversmann on 2006-11-10
and you can try VLC player, it has lots of codecs already with it.

don't forget to visit [www.getautomatix.com](www.getautomatix.com) if you want all these things done for you easily.

---

### Post by EvilAngel on 2006-11-12
MPlayer is not able to manage the file.

I tried with other vids but always the same problem.

Only MPEG vids are opened...:confused:

---

### Post by kinematic on 2006-11-12
try xine....the xine-libs should have the xvid codec sine it is open-source.

---

