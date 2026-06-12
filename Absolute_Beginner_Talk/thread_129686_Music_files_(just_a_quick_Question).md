---
title: "Music files (just a quick Question)"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by SonAsylum on 2006-02-14
I was just wondering what files are supported by Ubuntu out of the box. I am getting ready to pull some of my music from my other computer to the one that is now running Ubuntu and i would like to know which file format i should convert them to they are now in WMA and i am sure that Ubuntu doesn't support that.

---

### Post by Lord Illidan on 2006-02-14
Ubuntu can play wmas when you install the w32codecs package.. That way, you avoid having to convert them back to another format.

Otherwise have a look at ogg, or mp3.

---

### Post by SonAsylum on 2006-02-14
Hmm that is interesting i will look in to that. As far as mp3 i thought that that was not supported.

---

### Post by ajgreeny on 2006-02-14
SonAsylum, I think you're right about mp3 support but it is easy to add support for mp3 playback and writing by getting lame from synaptic.
On my box I have gstreamer0.8-lame, liblame0 and lame.  I don't really know if all 3 are needed, but they don't conflict so I've left them where they are.

---

