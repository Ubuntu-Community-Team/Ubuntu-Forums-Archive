---
title: "Java and multiple sound streams"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Potted Meat on 2007-05-20
Hello.  Up until now I've been able to find everything I needed to know by using these forums.

My problem:

I can use multiple sound streams such as playing an mp3 while watching a flash movie on youtube etc.  However, when I am playing an online Java game, the game seems to use the sound system exclusively.  Anytime I try to play an mp3 while the game is running I get the error:  "Could not open audio/system device: > no sound"

If I try to watch a Youtube video with the game window up, the movie will play but with no sound.

Is there a way to set up the sound system so that I can use multiple streams while using Java?

I'm using Feisty, btw.

Thank you.

PM

---

### Post by Pragmatist on 2007-05-21
Looks like you need to use a feature of Alsa called "dmix".   Check out this page:

[http://www.linuxjournal.com/node/7391/print](http://www.linuxjournal.com/node/7391/print)

---

