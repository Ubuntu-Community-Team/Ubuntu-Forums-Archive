---
title: "Only Black screen on Video"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by TigerTail on 2007-06-05
Ive tried VLC and Totem media players and no matter what plugins i install all i get is a black video screen with some sound. I cant figure out how to make it work so ive been downloading videos on my ubuntu system and burning them on a cd to watch them on my windows computer. has this ever happend to anyone else? how can i fix this.

---

### Post by taurus on 2007-06-05
Are you running beryl by any chance?

---

### Post by TigerTail on 2007-06-05
No i am not running beryl. this is a fresh install of ubuntu.

---

### Post by TigerTail on 2007-06-06
Well Ubuntu very good indead just not my cup of tea. GUI is nice. Very peppy operating system. No adware or spyware to worry about. :) But alas I must revert back to the resource hungry windows vista it was a nice trial run and will make for a decent review. as soon as i finish my software review page i will post the link here and you guys can give feedback or tell me im an idiot whichever suits you.

---

### Post by swoll1980 on 2007-06-06
You need to install the codecs. I used automatix2 just go to there web site it installs automaticly then go to applications>system tools>automatix . In the automatix go to codecs.
It's pretty self explanatory.

---

### Post by kittyhawk63 on 2007-06-06
> **TigerTail said:**
> Ive tried VLC and Totem media players and no matter what plugins i install all i get is a black video screen with some sound. I cant figure out how to make it work so ive been downloading videos on my ubuntu system and burning them on a cd to watch them on my windows computer. has this ever happend to anyone else? how can i fix this.

This worked for me. Just be sure to follow the instructions carefully. It will tell you to install Greasemonkey into Firefox.
kh
[http://www.mepislovers.org/forums/showthread.php?t=5511](http://www.mepislovers.org/forums/showthread.php?t=5511)

---

### Post by TigerTail on 2007-06-06
I did install the codecs off of the automatix2 program with no avail. I will try the link thanks for the help. Ive decided to keep ubuntu on my compaq computer. I am doing reviews for ubuntu vs vista right now. I need to put a better video card in so that i can test out the beryl.

---

### Post by WebDrake on 2007-06-07
I don't believe this is a codec issue as it has shown up on my computer which, only days ago, was happily playing video.

I don't recall if there were any recent updates .... which might be responsible?

Whether I try to open video with kaffeine or Totem or whatever, I get sound, but the picture is black.

---

### Post by Romericus on 2007-06-07
> **taurus said:**
> Are you running beryl by any chance?

I'm having the same problem, but only when I'm running beryl.  I hate having to disable beryl when I want to watch a video.  Is there a plugin or a fix for this problem?

---

### Post by Kulgan on 2007-06-07
> **Romericus said:**
> I'm having the same problem, but only when I'm running beryl.  I hate having to disable beryl when I want to watch a video.  Is there a plugin or a fix for this problem?

There are settings you have to change for Totem, at least. Run "gstreamer-properties" and under the Video tab select the "No Xv" option. This uses the CPU instead of the GPU for video processing, and the quality deteriorates accordingly. When it's just you wanting to watch a clip (hehe), it's fine, but if you want to, say, watch a movie with multiple people, it might still be worth turning beryl off and switching back the the GPU (whatever it was before you changed it - probably autodetect).

-K

---

