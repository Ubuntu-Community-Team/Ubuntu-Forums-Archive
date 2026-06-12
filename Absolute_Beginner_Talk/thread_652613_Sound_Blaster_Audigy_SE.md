---
title: "Sound Blaster Audigy SE"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by ntowakbh on 2007-12-28
I just bought a Sound blaster Audigy SE sound card, and I managed to get my sound working from "System --> Preferences --> Sound," however, no matter what I set it to, I cannot get my microphone to work.

My options are:

CA0106
CA0106
CA0106
CA0106
ALC861 Analog
ALSA - Advanced Linux Sound Architecture
OSS - Open Sound System
Test Sound
Silence

Please, any help is greatly appreciated.

---

### Post by Perfect Storm on 2007-12-29
Try **alsamixer** in the terminal and see if the mic is muted/low.

---

### Post by ntowakbh on 2007-12-29
> **Artificial Intelligence said:**
> Try **alsamixer** in the terminal and see if the mic is muted/low.

Nope, it isn't.

---

### Post by ntowakbh on 2007-12-30
Posted to move thread to front, in addition now to the microphone not working, I can't here sound in web browsers.  No youtube videos, etc. (The browser problem has been there from when I first installed the card, I just haven't tried going to youtube since I installed the card)

EDIT: Fixed my problem with the sound in browser.  I just went to the system BIOS, and disabled on board audio.

---

### Post by ubudave on 2008-01-10
I am having the same issue.  Just wanted to give this a bump because I have almost got this system working just as I want it except for the sound problem.

---

### Post by ckamc on 2008-01-10
Also having the same issue, I like to use my mic because it also doubles as a line-in for all my tv and video game systems

---

### Post by ckamc on 2008-01-13
I just got my line-in to work, found that typing in alsamixer into terminal and messing with the VERY last settings helped get this to work, don't have a mic to test that portion tho.

---

### Post by Jimmey on 2008-01-13
Sorry, but I don't get it - 

If you've got no mic to test it, how do you know it works?

I'd really love to be able to record with my SB/SE.

Thanks

---

### Post by ckamc on 2008-01-14
well the port still works right?

because what its doing then is taking an external audio source and feeling it into the computers speakers.

makes sense to me.

---

### Post by nikoPSK on 2008-01-14
Well, as AI suggested, I had to bump up some channels. Could we have a screenshot of your alsamixer?

nikoPSK

---

### Post by stchman on 2008-01-14
> **ntowakbh said:**
> I just bought a Sound blaster Audigy SE sound card, and I managed to get my sound working from "System --> Preferences --> Sound," however, no matter what I set it to, I cannot get my microphone to work.

My options are:

CA0106
CA0106
CA0106
CA0106
ALC861 Analog
ALSA - Advanced Linux Sound Architecture
OSS - Open Sound System
Test Sound
Silence

Please, any help is greatly appreciated.

Set the sound card you want from this:

[http://www.stchman.com/mult_sound.html](http://www.stchman.com/mult_sound.html)

You can select the sound card from a list.

---

### Post by nikoPSK on 2008-01-14
> **stchman said:**
> Set the sound card you want from this:

[http://www.stchman.com/mult_sound.html](http://www.stchman.com/mult_sound.html)

You can select the sound card from a list.

Ah, thank you. lol, mine was an audigy. I seem to have told him that already though... :)

EDIT: oopsie... was thinking of another thread... sorry.

---

