---
title: "music question?"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-03-02
so i just added my entire library 35000 or so songs into banshee, and it was processing each one of them, but when it was done, the end result was about 4000 songs...

how come?

---

### Post by viviena on 2006-03-02
Just an idea... perhaps not all your music files are of the same encoding? I believe Ubuntu won't read .mp4 or .m4a files naturally, for example, so you need to install special decoders. Do you have any music files which aren't mp3?

That's just my guess. I had a similar problem when I tried to import my iTunes library into Rhythmbox -- it wouldn't recognise any of my .m4a files, only .mp3s and .ogg. If I remember correctly, I fixed that by installing the various faac/faad packages in Synaptic.

---

### Post by stalefries on 2006-03-02
sudo apt-get install gstreamer0.8-plugins-multiverse

That should work for Banshee, and Rhythmbox.

---

