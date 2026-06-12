---
title: "Reverse left and right desktop speakers"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by utannheim on 2008-02-03
Due to some physical constraints (mainly cable lengths :-() my speakers  are positioned on the wrong side of the monitor i.e. the speaker marked R is on the left and the speaker marked L is on the right. I know this is kinda silly, but is there some way to tell Ubuntu to reverse the sound channels so the speaker to the left of the monitor will play sound from the left channel? 

Thanks in advance

---

### Post by Lostincyberspace on 2008-02-04
You might be able to use pulse audio to do it, it can be downloaded here [http://www.pulseaudio.org/](http://www.pulseaudio.org/)
It can do a lot of things but I don't know exactly what to do.

---

### Post by thirdhaf on 2008-04-05
I was struggling with this myself and I found the following which may be useful if you are using ALSA.  First of all the ALSA FAQ is where I got this information: [http://alsa.opensrc.org/FAQ#How_can_I_tell_ALSA_to_swap_the_left_and_right_stereo_channels_on_my_soundcard.3F](http://alsa.opensrc.org/FAQ#How_can_I_tell_ALSA_to_swap_the_left_and_right_stereo_channels_on_my_soundcard.3F)

If you want the swap to work universally you need to create a file called 

```
/etc/asound.conf
```

In this file should be the following lines:

```
pcm.swapped {
    type         route
    slave.pcm    "cards.pcm.default"
    ttable.0.1   1
    ttable.1.0   1
}

pcm.default      pcm.swapped
```


And now you should be all set, hope this solves your problem.

---

