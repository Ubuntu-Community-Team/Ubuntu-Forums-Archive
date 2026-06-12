---
title: "[SOLVED] I have an sound problem"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Gigantesco on 2007-11-16
ok so here it is...
normally, i can listen to music and everything works fine but when i try to change the volumes between
my two speakers thought "volume control" it seems that it plays only on the left speaker...
i try headphones and the problem the same...

moreover, the sound that i get compare to windows it a little bit crapy..
there's softwares which can manage my sound and really control it?

thank a lot..

---

### Post by Inxsible on 2007-11-16
Lets start with the basic and obvious.

open up a terminal and type in ```
alsamixer
``` and make sure all of them are at max levels

---

### Post by Gigantesco on 2007-11-16
> **Inxsible said:**
> Lets start with the basic and obvious.

open up a terminal and type in ```
alsamixer
``` and make sure all of them are at max levels

i did that...

and i'll try to explain my problem:
i hear music in both speakers(right and left) but when i lowering the right strem in volume
control it do nothing. however, when i lowering the left stream, it all mute.
so i cant mute one speaker at the time..

---

### Post by tonymoloney on 2007-11-16
Sounds like you're playing a mono source through stereo speakers. Mono comes in through the left input.

---

### Post by Gigantesco on 2007-11-16
> **tonymoloney said:**
> Sounds like you're playing a mono source through stereo speakers. Mono comes in through the left input.
so how to change it to stereo?
becuase i had same problem with the headphones so it cant be the speakers problem

---

### Post by limac on 2007-11-16
or there is a chance that the kernel can't recognize your soundcard.

---

### Post by oilchangeguy on 2007-11-16
think am radio here. if the source is in mono, you can't change it to stereo. although some sources should allow you to simulate stereo.

---

### Post by limac on 2007-11-16
srry disregard my post.

---

### Post by Gigantesco on 2007-11-16
dont mind that problem solved. crapy connection and took care...

---

### Post by adamorjames on 2007-11-16
Ah, nice ending. A bit funny too :D

---

