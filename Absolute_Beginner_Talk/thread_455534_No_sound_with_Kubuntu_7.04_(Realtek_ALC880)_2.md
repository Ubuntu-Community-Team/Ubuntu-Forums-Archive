---
title: "No sound with Kubuntu 7.04 (Realtek ALC880) 2"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ehlolz on 2007-05-26
Hey guys,
 
 For some reason I've no sound with Kubuntu 7.04! I installed the Operating System about 2 hours ago, and have been playing round with the mixer and chords while discussing my problem with others on "Konversation"; however, I can't fix it! I fail to get sound. Funny thing though, when I plug the headphones into the mic input, I get sound- but only from the right side of my headphones. My computer details are below:
 
 Kubuntu 7.04
 
 When I type AlsaMixer within the terminal, I get the following information:
 
 Card: HDA ULI M5461 
 Chip: Realtek ALC880 
 View: [Playback] Capture All 
 Item: Headphone 
 
 What do I do? please help! I'm new to linux and have no idea what I'm doing.

Also posted same thread here (such a large forum): [http://ubuntuforums.org/showthread.php?p=2726037#post2726037](http://ubuntuforums.org/showthread.php?p=2726037#post2726037)

---

### Post by Happy_Man on 2007-05-26
how about changing item:headphone to item:master using ```
alsaconf
```?

EDIT: don't listen to me, Kubuntu doesn't have alsaconf... could swear that it did, though.

---

### Post by ehlolz on 2007-05-27
wtf? no one is able to help me with this problem? This is a linux problem guys? come on..

---

### Post by dbulante on 2007-05-31
I have the same sound card and have been very frustrated that I can't get it to work.  There seems to be a bug in ubuntu concerning this sound card.

---

### Post by BobLand on 2007-05-31
Take a look at this post and see if anything helps.  Sometimes you have to try things that are not so obvious and things that are very obvious.  

[http://ubuntuforums.org/showthread.php?t=456519&page=2](http://ubuntuforums.org/showthread.php?t=456519&page=2)

---

### Post by ugm6hr on 2007-06-01
> **ehlolz said:**
> Hey guys,
 
 For some reason I've no sound with Kubuntu 7.04! I installed the Operating System about 2 hours ago, and have been playing round with the mixer and chords while discussing my problem with others on "Konversation"; however, I can't fix it! I fail to get sound. Funny thing though, when I plug the headphones into the mic input, I get sound- but only from the right side of my headphones. My computer details are below:
 
 Kubuntu 7.04
 
 When I type AlsaMixer within the terminal, I get the following information:
 
 Card: HDA ULI M5461 
 Chip: Realtek ALC880 
 View: [Playback] Capture All 
 Item: Headphone 
 
 What do I do? please help! I'm new to linux and have no idea what I'm doing.

Also posted same thread here (such a large forum): [http://ubuntuforums.org/showthread.php?p=2726037#post2726037](http://ubuntuforums.org/showthread.php?p=2726037#post2726037)

Not sure about Kubuntu - but my post in this thread explains the solution for my Realtek soundcard in (X)Ubuntu:
[http://ubuntuforums.org/showthread.php?t=459360](http://ubuntuforums.org/showthread.php?t=459360)

Although - does *alsamixer* (lower case) do anything in Kubuntu?  AlsaMixer does nothing in Xubuntu.

---

### Post by Happy_Man on 2007-06-01
Yes.... alsamixer definitely works in Kubuntu. I just tried it.

---

### Post by Sparkster185 on 2007-06-01
Do you have an intel HDA sound card?

```

lspci -v | less

``` and search for audio.  If you see something like

> 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01

Then try this:

Add "options snd-hda-intel model=3stack" at the end of /etc/modprobe.d/alsa-base, and now sound works! Try it out! (I have a Toshiba Satellite A135-S4407).

---

### Post by dbulante on 2007-06-04
I know mine already has "options snd-hda-intel model=3stack" in the alsa-base file, and it still doesn't work.  In fact, I tried to just replace it with model=ALC880, and that did not do anything also.

---

