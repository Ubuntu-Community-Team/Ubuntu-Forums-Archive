---
title: "Acer Aspire 5050 Problems"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by KyyubiDX on 2007-07-16
Hi all,

I have an Acer Aspire 5050 with the following specifications:

AMD Turion 64 2.0 GHz/Cache 512 Kb
512 RAM DDR SDRAM
HDD 80 Gb
ATI Radeon Xpress 1100
Broadcom LAN
HD Audio Driver

I installed Ubuntu 7.04 Feisty Fawn yesterday but ran into some problems video/audio related.
Can anyone tell me where tog et the audio/video drivers?
I'd really apreciate it...

---

### Post by Happy_Man on 2007-07-16
What kind of problems?

---

### Post by KyyubiDX on 2007-07-16
no sound and no detection of my video hardware... any ideas?

---

### Post by overdrank on 2007-07-16
> **KyyubiDX said:**
> no sound and no detection of my video hardware... any ideas?

Hi have you tried this sticky
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by KyyubiDX on 2007-07-16
maybe i expressed myself wrongly (sorry) but what i meant to say was no audio and altough X starts and all it says i'm using a 16 megs video card (which is not correct for i am using a 128 MB shared mem one)

---

### Post by overdrank on 2007-07-16
> **KyyubiDX said:**
> maybe i expressed myself wrongly (sorry) but what i meant to say was no audio and altough X starts and all it says i'm using a 16 megs video card (which is not correct for i am using a 128 MB shared mem one)

Ok then you may find some help in this thread
[http://ubuntuforums.org/showthread.php?t=362525&highlight=x1100](http://ubuntuforums.org/showthread.php?t=362525&highlight=x1100)

---

### Post by KyyubiDX on 2007-07-16
seems cool.. i'll try it... what about the audio?

---

### Post by overdrank on 2007-07-16
> **KyyubiDX said:**
> seems cool.. i'll try it... what about the audio?

Could you post the output of  the command in the terminal
```
lspci
```

---

### Post by KyyubiDX on 2007-07-16
what am i supposed to find there that'll be useful?

---

### Post by overdrank on 2007-07-16
> **KyyubiDX said:**
> what am i supposed to find there that'll be useful?

It will tell us your sound card but you can search and find it. :popcorn:

---

### Post by KyyubiDX on 2007-07-16
nothing there that resembles a sound card... :S

---

### Post by KyyubiDX on 2007-07-16
also... i'm trying to activate "Proprietary drivers for devices (restricted)" but when i check the box activate it says deactivated.... what's wrong?

---

### Post by ugm6hr on 2007-07-16
I have the same laptop.

Have you activated the restricted drivers (for ATI)?  My screen works just fine as widescreen 1280x800 (default).

For sound - have you updated the kernel, or are you still running 2.6.20-15?  If you are still on 2.6.20-15, for sound - do the following:
```
alsamixer
```
Use the left/right arrow keys to find "Surround" in the new page that opens. Make sure it has a symbol "OO" (if it says "MM" - press "M" to unmute), then press the up arrow to maximise the volume.  It will then work.  Make sure that PCM is maximised as well.

To explain - this laptop labels the headphone socket as center speaker, and the laptop speakers as surround.  So you should be able to hear sounds already if you plug headphones in.

If you have updated the kernel already, then you may have to recompile alsa - try this for advice:
[http://ubuntuforums.org/showthread.php?t=457011&page=2](http://ubuntuforums.org/showthread.php?t=457011&page=2) (post #16)

---

### Post by ugm6hr on 2007-07-16
> **KyyubiDX said:**
> also... i'm trying to activate "Proprietary drivers for devices (restricted)" but when i check the box activate it says deactivated.... what's wrong?
That's bizarre. You should be able to check the box, and it should install (after giving you some kind of warning about using them).  That's what I did.

---

### Post by KyyubiDX on 2007-07-16
it doens't let me check... its sooooo weird... any ideas?

p.s. (edit) => sound is up and working... yay
     (edit2) => now i have to get the alsa drivers to work

---

### Post by KyyubiDX on 2007-07-16
this is so freaking crazy... i updated the drivers of my sound card (or tried) for now i know it is a realtek 883 something... and during the install it gave some wierd errors and when i find my self the alsamixer is gone and after rebooting X it won't even allow me to log-in... ins't there any one who can help?

---

