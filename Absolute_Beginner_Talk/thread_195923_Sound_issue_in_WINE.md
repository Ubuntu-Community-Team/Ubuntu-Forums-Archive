---
title: "Sound issue in WINE"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by TheRealSol on 2006-06-13
I am unable to get any form of sound to work in WINE except an occasional "blip" on the launch of an application. I ran winecfg through the command line and here is the default sound it set along with an error message that came up on the command line:

[http://i61.photobucket.com/albums/h46/SunaOrLater/wine.png](http://i61.photobucket.com/albums/h46/SunaOrLater/wine.png)

---

### Post by givré on 2006-06-13
oss is the old sound system in linux, it can only manage one sound pipe (until your sound card don"t support mixer, which is the majority of the card), so try the alsa driver, but it don't work always really good with wine, so if it doesn't work, stop all the other sound before launching your wine apps with the oss driver

---

### Post by TheRealSol on 2006-06-13
There's a linux command I can run in the terminal that kills all the sound, right?

---

