---
title: "Creative Sound Blaster Audigy 2 no sound"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by oblivioncth on 2008-03-24
I have a Creative Soundblaster Audigy 2 sound card. I just became a linux user today at around 5:00 pm so I don't know much. In Ubuntu, Mute is not on, the cables are pluged in, everything. But there is no sound. Ubuntu sees the card in the hardware manager. On the web site there are no drivers for it for linux so I don't know what to do. I don't even know if the drivers are the issue. SO USED TO WINDOWS.

Any help is appreciated


SOUND!!!!!  :guitar: :mad::-({|=

---

### Post by oblivioncth on 2008-03-24
I re-posted this for a better tittle. If the moderators see this I ask them to please delete my "No sound in Ubuntu" Post


I have a Creative Soundblaster Audigy 2 sound card. I just became a linux user today at around 5:00 pm so I don't know much. In Ubuntu, Mute is not on, the cables are pluged in, everything. But there is no sound. Ubuntu sees the card in the hardware manager. On the web site there are no drivers for it for linux so I don't know what to do. I don't even know if the drivers are the issue. 

Any help is appreciated


SOUND!!!!!  :guitar: :mad:

---

### Post by scragar on 2008-03-24
some tips in this thread:
[http://ubuntuforums.org/showthread.php?t=724665](http://ubuntuforums.org/showthread.php?t=724665)

---

### Post by Samurai Penguin on 2008-03-24
I use an Audigy1 card, here's what I had to do to get sound ...

Volume Control > File > Change Device > select the Audigy card
Volume Control > Switches Tab > uncheck Audigy Analog/Digital Output Jack

---

### Post by pugofdestiny on 2008-03-24
Im not postitive this will work but when i play a game and don't get sound i Do the following...

1) Goto your top bar click Applications > Accessories > Terminal.
2) type killall esd
3)type sudo -i
4)you will be prompted for your user password type it in you will not be able to see it typing but it is typing.
5)type echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
6)type exit

Now it should work not postitive it will work though im just going on guess's because when i loose sound on games like wolfenstein et thats what i do and it fix's it. hope it helps. :guitar:

---

### Post by p_quarles on 2008-03-24
Threads merged. Please do not post more than once about each problem.

---

### Post by stchman on 2008-03-25
> **oblivioncth said:**
> I have a Creative Soundblaster Audigy 2 sound card. I just became a linux user today at around 5:00 pm so I don't know much. In Ubuntu, Mute is not on, the cables are pluged in, everything. But there is no sound. Ubuntu sees the card in the hardware manager. On the web site there are no drivers for it for linux so I don't know what to do. I don't even know if the drivers are the issue. SO USED TO WINDOWS.

Any help is appreciated


SOUND!!!!!  :guitar: :mad::-({|=

I had the same problem with my Audigy 2 on my AC97 disabled motherboard.  Make your Audigy2 the default sound card.

[http://www.stchman.com/mult_sound.html](http://www.stchman.com/mult_sound.html)

This worked for me.  Ubuntu supports the Audigy 2 OOB.

---

