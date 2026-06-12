---
title: "this is driving me NUTS"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by infernus_crusher on 2007-10-31
i've asked this so many times in a lot of threads but nobody seems to be answering at all.

how do i capture any sound that comes out from my SOUND CARD?

---

### Post by skymera on 2007-10-31
usually you plug in speakers and the sound plays.

what problem ar you having? more detail :)

---

### Post by Salpiche on 2007-10-31
what do you mean by capture? do you want to record a sound or stream i/e from a website? maybe you need to be more specific as what do you want to do.

---

### Post by Dr Small on 2007-10-31
I think he wants to capture the sound, that is being played from the sound card, example, like streaming audio or audio in a movie, and be able to capture a portion of it and save it.

I would also like to be able to do this.

Dr Small

---

### Post by kingpoiuy on 2007-10-31
Audacity will do it.  Install Audacity and try it.  If you have problems with Audacity post your exact issue.

---

### Post by Dr Small on 2007-10-31
I myself have tried Audacity, but it will not record on any of the input devices, so that one never worked for me..

---

### Post by wigg on 2007-10-31
Try "Audacity" it's a great tool for recording audio.  You can record what is coming out of your speakers by selecting the stereo output.  On my ubuntu box at work it's labeled: 

[COLOR="Blue"]"HDA Intel: ALC262 Analog (hw:0,0)"[/COLOR]

---

### Post by infernus_crusher on 2007-11-01
I've tried audacity. I set ALSA: Default as my playback device and ALSA HDA Intel ALC861 Analog as my recording device.

Now, I do this two different ways, and they give me two different results:

1. I press Record in Audacity FIRST, and then open Rhythmbox and play music, and Audacity records nothing at all.

2. I play a music in Rhythmbox FIRST and then press the Record button on Audacity. And I got this error message: "Error while opening sound device. Please check the input device setting and the project sample rate"

---

### Post by hoges on 2007-11-01
The two programs are fighting for control of the sound card. Which sound card do you have?

---

### Post by infernus_crusher on 2007-11-01
I'm not sure how to check sound cards, but in the drop down list of playback and record devices in Audacity there are:
1. OSS: /dev/dsp : I've used this for recording at there's an endless beeping sound
2. ALSA HDA Intel ALC861 Analog
3. ALSA HDA Intel Si3054 Modem
4. ALSA default
5. ALSA front
6. ALSA surround40
7. ALSA surround51
8. ALSA surround71
9. ALSA modem
10. ALSA phoneline

---

### Post by discmaster on 2007-11-01
Don't feel bad, infernus_crusher; I have been fighting this one since April 07! Just today I connected a speaker out to line in on the sound card (not really the way you are supposed to do it) & it recorded w/ audacity. I can verify the recording from the level meters. However, I can't get the recorded sound to play back!   :confused:

---

### Post by infernus_crusher on 2007-11-02
Really? That's bad... I guess I'll just give up then.

I have a program that would do it in Windows, it's called ReplayMusic. But it clashes with VLC player (which I use to play the DVD). By having ReplayMusic record at the same time VLC plays the DVD, the DVD plays very choppily.

---

