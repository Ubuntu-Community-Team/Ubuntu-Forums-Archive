---
title: "Creative Sound Blaster Digital Music SX"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by umpalumap1985 on 2006-11-05
Okay.  I know you've heard this before.  I am yet another Linux noob.
That said, i have a small issue with my usb sound card, the Sound Blaster digital Music SX.  If you haven't heard of it, it's probably because it's only (as far as i know) available here in japan.  Anyway, I got the thing working, the only problem is poor sound quality. . .crackly, distorted, the whole nine yards.  But what really confuses me is that Skype (so far the only app i've noticed to do this) sounds just fine.  Sharp, crisp, clear sound.  But in every other app, music players, even Gaim, the sound is all crappy.  Any help would be appreciated, and thank you in advance.

---

### Post by minichocobo on 2007-08-27
This card only supports 48KHz or 96KHz  sound playback. However, most audio files use 44.1KHz sampling rate, which the sound card does not support at all.

    You have to configure alsa  to resample the audio to 48KHz ( or 96 KHz) so that the sound card can playback normally.

---

### Post by robertopisa on 2007-11-03
Creative Sound Blaster Digital Music SX supports  44100, 48000 and 96000, 

I'm sure since I use its digital output in my DAC and it display 44100 when playing WAV, for example.

Here is how to make the SX work under Ubuntu

First, install ALSA as sound system.

Second, check with a wav file if you hear correctly the sound
aplay -D hw:1,1 file.wav

Third, add the following lines to your .asoundrc file (if not, create it)
pcm.!default {
        type hw
        card 1
        device 1
}

Is it possible that your USB soundcard is detected differently from hw:1,1.

In this case, run
cat /proc/asound/devices

and try to replace hw:1,1 above with hw:x,y for each line of the form
[x- y]: digital audio playback
that you find in devices. Here x and y are numbers (tipically 0,1,2).

Cheers
Roberto

---

