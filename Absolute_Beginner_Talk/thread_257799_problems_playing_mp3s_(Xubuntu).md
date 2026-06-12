---
title: "problems playing mp3s (Xubuntu)"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2006-09-15
I have a compaq pressario 1200 P3. Xubuntu Dapper

I can't play mp3s using either XFMEdia, kaffeine or Rhythmbox. (nothing happens when opening a file). I can play DVDs perfectly with kaffeine.

When importing an mp3 file into the library this message appears:
```
the file is not an audio stream | file:///home/maarten/Music/song.mp3
```

What can I do to solve this?

---

### Post by deadgobby on 2006-09-15
Have you tried XMMS player? It sound like you may have install the codecs, because you can play DVD's.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Gobby

---

### Post by stroopwafel on 2006-09-16
it works now. Thanks!

I installed the gstreamer packages on [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

can someone explain why I needed to do this before playing a "standard format" like mp3?

should i install the following too?
gxine
libxine-main1
libxine-extracodecs
ogle
ogle-gui
w32codecs 

what are the pro-s and cons for just installing extra packages?

Thanks so much,

Maarten.

---

### Post by 3rdalbum on 2006-09-16
While MP3 is a "standard format", it's owned by a company called Thompson Multimedia. Microsoft and Apple pay thousands of dollars a year to legally include MP3 support with their operating systems. They can afford it because they're getting revenue from selling their OSs; since Ubuntu is free, there's no revenue stream to use to pay for the codecs licensing.

And yes, install the other codecs you mention.

I recommend you install GXine and MPlayer too, as these players have different strengths and weaknesses. Together with Totem Gstreamer and the w32codecs, you'll be able to play anything.

---

