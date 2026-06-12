---
title: "No sound?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-09-11
Hey there ive run into a problem recently, when tyring to play music with rythmbox i cant hear any music or sound, however when say watching a video in youtube or anything else i can hear sound

its kinda random too, usually i can listen to music, however every now and then i cant hear music with rythmbox specifically, feedback much appreciated, thanks

---

### Post by ijason on 2007-09-11
i'm not sure if this will help with every sound problem, but i was getting some sound issues with Wolfenstein ET. the solution was to open a terminal and then :

  killall esd

and then you run the applicatation. when you're done with the application and if system sound doesn't return, open terminal again and this time :

  esd

you should hear your speakers make a little tone chirp to let you know it's restarting the sound.

good luck!

---

