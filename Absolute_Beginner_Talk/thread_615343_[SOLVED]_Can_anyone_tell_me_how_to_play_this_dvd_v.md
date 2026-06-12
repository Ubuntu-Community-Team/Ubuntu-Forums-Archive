---
title: "[SOLVED] Can anyone tell me how to play this dvd video?"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by bhold on 2007-11-17
I have a dvd, supposedly has some videos on it. It won't play. Xine gives an error message - No demuxer, stream not recognized. No luck with Totem either. I've spent several hours reading the Ubuntu community docs and forum and installing recommended codecs, libs, plugins, restricteds, etc... It still won't play.

The files on this dvd look as follows in case it helps...

Folder AUDIO_TS (empty)
Folder VIDEO_TS (contains .BUP, .IFO, and .VOB files)

Does this provide information about what software is required to play? If so, please enlighten me.

---

### Post by schauerlich on 2007-11-17
DVDs use proprietary codecs not included in Ubuntu. Here's a howto:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by bhold on 2007-11-17
Thanks, worked great! Specifically, what I did was...

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine
sudo /usr/share/doc/libdvdread3/install-css.sh

(Message indicated that totem-gstreamer was removed, I assume that is not needed if you install totem-xine.).

---

