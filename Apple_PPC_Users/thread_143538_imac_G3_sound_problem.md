---
title: "imac G3 sound problem"
date: 2006-03-12
forum: Apple PPC Users
---

### Post by grumpyoldtech on 2006-03-12
Imac G3 bondi 
233Mhz 
160Mb Ram
6Mb Video Ram
40 Gb hardrive

the sound detects a a burgandy mac Whats a burgandy mac?
 
the sound does make sound and I can play music if I plug headphone into the jack.  the headphone don't work but the speakers in the case do.  they are slightly distorted. I would like to be able to use external speakers.

first is there a better driver in ubuntu ppc for this computer
or  has someone found away to make this driver work properly  

I'm trying to biuld a box just for music so good sound wound be nice. 
I have also biult a 333 imac and have the same sound problems with it.
Thanks in advance

---

### Post by linear on 2006-03-12
Burgundy refers to the chipset. G3's have sound problems. You can read about it [here]("https://wiki.ubuntu.com/MartinEricRacine").

---

### Post by 3rdalbum on 2006-03-13
You shouldn't be having problems with getting sound OUT of the iMac. I've got the 333 and there's no problems there.

Here's a thought: When I plug something into a headphones port, the PCM-2 channel of the OSS Mixer becomes muted. The PCM-2 channel is basically all sound that is generated within the computer. Have you tried plugging in your external speakers, going into the mixer and turning that channel back up again?

Personally, I have a little Volume Control applet on my GNOME panel, set to the PCM-2 channel, in case I accidentally start up with something plugged into my headphone or Line In port.

---

### Post by fraterf93 on 2006-03-22
Hi I have a similar problem with my iMac G3 600 MHz.  All of the system sounds work, but I get no audio from playing a CD, Or any ogg files I've ripped from CD.  And I'm not usind any headphones, just the speakers that come with the iMac.  Personally, I can't sit in front of a computer and not have music playing.  This is a serious obstacle to me dropping OS X in favor of Linux(Well theres Java and DVD playback as well!).  Anyone know if Dapper Drake fixes this problem?

---

### Post by revdev on 2006-05-17
i had this problem as well, and found a quick solution. i plugged a headphone spliiter (anything will work, though) into the jack on the side, and then plugged my external speakers into one of the jacks on the front. then in alsamixer i turned headphones all the way down and master up, and now i get sound only from external speakers.

---

