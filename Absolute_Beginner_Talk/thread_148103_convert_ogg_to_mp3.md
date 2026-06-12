---
title: "convert ogg to mp3"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by nala on 2006-03-21
How to I convert .ogg files to .mp3 files? I have an mp3 player that only plays .wav  or .mp3 files. Since it has very limited storage capacity, I would prefer to use the .mp3 format.

I would also be happy to learn how to get Ubuntu to allow me to rip songs from my CDs  as .mp3 files instead of .ogg. I followed the directions in the startup guide, but every time I try to rip a song as .mp3 Sound Juicer crashes. ( I'm also having problems with VLC, which refuses to play sound. Are the problems related?)

---

### Post by Aewheros on 2006-03-21
The general advice is: Never transcode between two lossy audio formats. Due to  differences in compression methods you will loose sound quality.

But since you need mp3 for your music player, I guess there isn't much choice. Unless you can get/rip original mp3-files instead of converting from vorbis.

I can recommend *Grip audio ripper* for ripping and encoding to mp3.

---

### Post by nala on 2006-03-21
I suppose I can always re-rip the music from my CD colelction. =/ Thanks for the recommendation. I'll try it out.

---

### Post by IYY on 2006-03-21
I'd suggest re-ripping, for the same reason as stated above. You will certainly lose some quality. However, it is very easy to convert ogg to mp3: You convert from ogg to wav using "oggdec", and convert wav to mp3 using "lame".

---

