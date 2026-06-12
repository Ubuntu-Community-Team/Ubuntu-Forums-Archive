---
title: "MPEG 1 Layer II"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by hundaco59 on 2007-03-18
I am a relatively new convert to linux.  I am using Ubuntu Edgy on both my laptop and home desktop.
What I am trying to find is a plugin or a player that will play and or convert MPEG 1 Layer II to ogg or mp3 (MPEG 1 layer III).
Note:   MPEG 1 layer II is a proprietry codec owned by Musicam.   It is not MPEG 2.
I am also trying to connect to a hardware audio codec which is multicasting in layer II.


> 

There are 3 rules for making a smooth landing.   Unfortunately no one knows what they are.

---

### Post by mykalreborn on 2007-03-19
```
sudo apt-get install gstreamer0.8-mad
```

this will allow you to play the files. i don't know about encoding in ogg, though.

---

