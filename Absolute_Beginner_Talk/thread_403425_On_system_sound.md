---
title: "On system sound"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-04-07
[COLOR="DarkRed"]Hello, I am still trying to work with sound in 3 German Programs but I was wondering, in SYSTEM-PREFERENCES-SOUND-DEVICES-AUDIO CONFERENCING I am running the test on the sound capture and I am hearing nothing, these are my selections.
-OSS open sound systme
-ALSA-advanced Linus Sound Arhive
-ES1371 DAC2/ADC

I am getting no sound at all in testing the sound capture,

Should I be???

Sherri[/COLOR]

---

### Post by heimo on 2007-04-07
> **delilahjed44 said:**
> [COLOR=DarkRed]
I am getting no sound at all in testing the sound capture,
[/COLOR]

As far as I know, no. I don't know how this capture test should work, but it has never given me any sound, and my microphone is working fine.

---

### Post by delilahjed44 on 2007-04-07
> **heimo said:**
> As far as I know, no. I don't know how this capture test should work, but it has never given me any sound, and my microphone is working fine.

Hey, thanks for answering, my mic was there before I installed Ubuntu of course, but untill I can actually get my programs running I will not be sure how to test the mic.  Its just a cheapie plug in for my German games.  Has yours always worked>

Sherri

---

### Post by heimo on 2007-04-07
I've two soundcards, integrated and external USB. I never got the external to work with my mic, but with the integrated one it works fine. I did have to turn up microphone "volume" slider in alsamixer and select it as an input source (eg. Volume Controller -> Options -> Input source -> Mic -- these settings may be different for different cards). Sometimes you also need to select correct device in a program you'll be using to capture audio.

---

