---
title: "Recording"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by xstevex on 2007-05-11
I have audacity installed, and know how to use it

My microphone and line in are both on full volume

i have chosen every available input in audacity and yet none of them record anything just a flat line.

any help? 

(i have a realtek ALC883)

---

### Post by deepwave on 2007-05-11
Did you try adjusting the mic volume in audacity itself?
How about trying to running audacity with aoss?
```
aoss audacity
```

---

### Post by xstevex on 2007-05-13
tried both

neither worked.

:(

---

### Post by deepwave on 2007-05-18
Hmm... I'm not sure if [this will help]("http://opensourcegamer.blogspot.com/2007/02/running-audacity-under-ubuntu-610-linux.html"), but thats what I did when I could not get audacity to work correctly.

Mind you I have a Intel 82801G (ICH7), and not realtek ALC883.  Maybe its a problem with recording in general with that sound card?

Also maybe setting the Device and Playback to OSS [/dev/dsp] in the Preferences/Audio I/O might help, when running audacity with aoss.

---

