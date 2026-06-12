---
title: "Amarok wont play anything"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-19
when i click on a song to play it says theres no availible decodeer.

yet Rhythmbox plays them all fine.

what am i missing?

---

### Post by orange2k on 2007-10-19
I used EasyUbuntu for this.

EasyUbuntu is a utility used for installing extra codecs - something like Automatix, just better...
As I recall, Amarok uses a different set of codecs for mp3 playback, not gstreamer like Rythmbox...

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by skymera on 2007-10-19
but surely i dont need codecs if rhythmbox can play everything? =S

thanks for tip tho

---

### Post by FredB on 2007-10-19
> **skymera said:**
> when i click on a song to play it says theres no availible decodeer.

yet Rhythmbox plays them all fine.

what am i missing?

```
sudo apt-get install ubuntu-restricted-extras 
```

Just guessing, of course.

---

### Post by orange2k on 2007-10-19
> **skymera said:**
> but surely i dont need codecs if rhythmbox can play everything? =S


Yes you do. Amarok and K3b require additional codecs to be able to handle mp3.
Amarok uses the xine engine which doesn`t run on gstreamer set of codecs...

---

### Post by Vandread on 2007-10-19
I was going to post the same thing. It was weird because in 7.04 I only had problems with mp3 playback and that was easily fixed but it doesnt play anything not even streams. I brought laptop to work, will try the tips you guys posted.

---

### Post by pointone on 2007-10-19
You can tell Amarok to use GStreamer instead of xine in Amarok preferences under "engine".

---

### Post by BoredOutOfMyMind on 2007-10-20
> **pointone said:**
> You can tell Amarok to use GStreamer instead of xine in Amarok preferences under "engine".


The only option is Xine.  mp3 has been working perfect for the last 3 weeks, and all of a sudden many of us have the same problem....Google and Search ubuntuforums show this is a common new bug. 

Ugly since this is supposed to be more stable Long term. 
:mad:

---

### Post by Ender429 on 2007-10-20
Is there a decoder/codec that i can enable or install that will allow for amarok to playback AAC/.m4p files??

---

### Post by GlennW on 2007-10-24
I have the same issue. Amarok's the best music player out there plus it does so much more than just play music.

So where's the decoder? Someone's gotta know something.....

---

### Post by Cygnus on 2007-10-24
I can add that I had Amarok playing everything except streams ( like the last.fm streams ), but it was fixed by installing the package *libxine1-plugins* on Kubuntu 7.10.

---

### Post by GlennW on 2007-10-24
> **Cygnus said:**
> I can add that I had Amarok playing everything except streams ( like the last.fm streams ), but it was fixed by installing the package *libxine1-plugins* on Kubuntu 7.10.

:):):):)

That's it!! Amarok is right as rain now!! It not playing was the only "fly in the ointment" and now that it's fixed I can happily continue converting all my friends and family.

Very grateful - thanks!!

---

### Post by GlennW on 2007-10-25
Well, not so happy now. :confused: :confused:

I don't have streaming video (no audio with that either) and in the process of attempting to rectify that by "apt-get"-ing, I lost Amarok's audio. At least now there's no error message. I can see that Amarok is playing the file but there's just no audio. I've checked the Sound settings (System>Preferences>Sound), testing each setting. The only ones that function when testing are ES1371 DAC1 and 2. Amarok doesn't have those options available. I tried installing *libxine1-plugins* again but to no avail.

Any suggestions??

---

