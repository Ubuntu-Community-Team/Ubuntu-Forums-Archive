---
title: "Play movie DVD's ..."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-25
I have a movie DVD that has several Movies on it.  Totem plays just the first movie.
When I insert the DVD in a regular DVD player, it starts with a menu where I can select the movie to play.  Totem does not do this - at least I can't figure out how.

Is Totem the only player we have for playing movie DVD's?  How does one play the other movies on the same disc?

Thanks

Carl

---

### Post by Incense on 2007-10-25
VLC will play the menus. 

```
sudo apt-get install vlc
```

---

### Post by Pumalite on 2007-10-25
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by julian67 on 2007-10-25
> **cwmoser said:**
> I have a movie DVD that has several Movies on it.  Totem plays just the first movie.
When I insert the DVD in a regular DVD player, it starts with a menu where I can select the movie to play.  Totem does not do this - at least I can't figure out how.

Is Totem the only player we have for playing movie DVD's?  How does one play the other movies on the same disc?

Thanks

Carl

Totem can play DVD menus, but not while it is using Gstreamer backend. You can replace totem with totem-xine and also add w32 codecs, libxine1-ffmpeg, libdvdcss2 and libdvdread. See the other reply with the link to Medibuntu to get these. Totem with xine backend is really a nice player and fits in very well with the rest of the Ubuntu desktop, using the same look and feel. You can of course choose a different player like VLC or mplayer or Kaffeine or Xine player itself.

---

### Post by cwmoser on 2007-10-26
How do you associate VLC such that it automatically runs instead of Totem when a DVD is inserted?

Carl

---

