---
title: "Mp3 Ripping"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by fraser_m on 2007-08-06
I have installed lame
```
sudo apt-get install lame
```
but when I go to the preferences in Banshee it only shows FLAC OGG and Waveform PCM.

What have I done wrong?

---

### Post by Jimmyfj on 2007-08-06
If you install Audacity you will be able to convert files into the MP3 format

Programs>Add/Remove>Music & Videos>Audacity

The program is easy to use and make files sound well

---

### Post by Nike T on 2007-08-06
If you're going to use anything to encode to mp3, don't rip to Ogg, rip to FLAC and then encode to mp3, as transcoding from ogg will lose quality

---

### Post by Hobo Joe on 2007-08-06
Is there any program that will rip straight from the CD to an MP3?

---

### Post by macogw on 2007-08-06
Install the ubuntu-restricted-extras and it should work.  I spent all day on this with Sound Juicer (Banshee uses SJ for ripping), and tried lame and gstreamer0.8-lame without it working, but ubuntu-restricted-extras got it working (restart your ripping program after installing it)

---

### Post by MetalMusicAddict on 2007-08-06
macogw's way should be correct. Alternatively you could give the Grip HOW-TO in my sig a look.

---

