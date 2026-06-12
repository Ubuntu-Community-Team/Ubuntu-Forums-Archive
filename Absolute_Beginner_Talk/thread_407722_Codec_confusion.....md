---
title: "Codec confusion...."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-04-12
I'm still very new to players & codecs in Ubuntu, so please bear with me...

I have two video clips. One is a .mp4 the other is a .mpg. I'm using Totem to play both the files. The .mpg plays with sound, but no picture, the .mp4 plays with picture, but no sound?! :confused:

---

### Post by Bachstelze on 2007-04-12
Try to use Xine instead of GStreamer as a backend for Totem :

```
sudo apt-get install totem-xine
```

---

### Post by annda on 2007-04-12
have you tried playing those files with mplayer and/or vlc? in my experience, they have much better support for various formats.

---

### Post by Stickymaddness on 2007-04-12
> sudo apt-get install totem-xine

Is there anyway to reverse that? Nothing plays in totem now...doesn't really matter I guess...

> **annda said:**
> have you tried playing those files with mplayer and/or vlc? in my experience, they have much better support for various formats.

Awesome thanks, I didn't think to get VLC, even though I used to use it in windows!! Thanks, I'll just use VLC to play everything...

---

### Post by az on 2007-04-12
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

