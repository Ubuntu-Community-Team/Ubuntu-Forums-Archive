---
title: "Amateur Radio"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by thelemech on 2007-06-20
I just installed Xubuntu from the synaptic console- and noticed something called amateur radio- Is this what I think it is?- a way to turn my PC into a internet radio station?

---

### Post by Jerry N on 2007-06-20
The function of those amateur radio application programs is to support various activities of licensed amateur radio operators.  They also provide computer aided design and analysis tools for the design of electronics, particularly those associated with transmission and reception of information.

Jerry

---

### Post by thelemech on 2007-06-20
Interesting!! Thanks.

---

### Post by tgalati4 on 2007-06-20
Of course, you can install icecast or Muse and create an internet radio station.  It's not that difficult.

sudo apt-get install icecast
sudo apt-get install muse

Start playing around and you will get the hand of streaming audio from your computer.

---

### Post by thelemech on 2007-06-20
Excellent- I have more than 60 Gb of music on another computer  that I would love to DJ!

Ubuntu is getting more interesting all the time.

---

### Post by MNO on 2007-06-25
Short note:

MuSE (the one from dynebolic)  does not exist for Debian, you need to install from source.

MusE (the one in the repository) is a sequenser, not a streaming encoder.

Icecast2 is only a streaming server and it needs an encoder to it. Use Ices2, Darkice, Darksnow or MuSE for that. I'm wondering why none of these are available in the Ubuntu Studio repo, 

Anyone know why?

M.

---

