---
title: "I've got no sound..."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by enchance on 2007-03-09
I've got no sound on my ubuntu 6.10. I just installed it on my laptop. Is easyubuntu gonna cut it? :confused:

---

### Post by PartisanEntity on 2007-03-09
Try to play an audio file, also try to play an audio cd, and finally try to play any sound/video file off any website, lets us know the results.

---

### Post by enchance on 2007-03-09
Okay, I tried running an mp3 file but still nothing. Did you guys have sound after immediately installing and updating your Ubuntu?

---

### Post by pandu.rs on 2007-03-09
do u get some sound during login or logoff?

to play mp3 files u need to install codecs
[https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9](https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9)

---

### Post by melancholeric on 2007-03-09
> **enchance said:**
> Okay, I tried running an mp3 file but still nothing. Did you guys have sound after immediately installing and updating your Ubuntu?
MP3 is not supported out of the box. You need to install the codecs first.

Then again, it might be an actual audio problem as well, but you need to test it with say audio cd or an ogg or waveform audio file first.

I've actually never had sound working properly, out of the box, neither on ubuntu or debian. In my case I believe the problem is having two sound devices, but I only want to use the other, and it defaults to using the wrong one.

Try opening volume control, and File -> Change Device.

If that doesn't help, run alsaconf. 

sudo alsaconf

if you don't have it, sudo apt-get install alsaconf

---

