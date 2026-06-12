---
title: "scratchy sound during games"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Hybrid86 on 2007-07-26
I have a Dell inspiron 8600 laptop. I recently installed ubuntu, and am loving it. However, the sound has become an issue. When I am either staring up or listening to music, the sound is fine. however, when I play a game (neverball or zsnes for example), the sound is very scratchy. Is there a fix for this?

---

### Post by srt4play on 2007-07-26
Try installing alsa-oss in synaptic.

---

### Post by JPorter on 2007-07-26
When you say "scratchy", do you mean that it's distorted?

Your PCM volume may be too high, and as a result there's a gain distortion problem with the sound card's output stage.


To check, go to the terminal and type [FONT="Courier New"]alsamixer[/FONT]

Use the left/right arrows to go to each channel, up/down to increase or decrease the volume.  Set the PCM volume to 0.00 gain.

Hit the Q key to exit.


If you want to save this so it persists through reboot as the "default", type the following at the terminal prompt:

[FONT="Courier New"]sudo alsactl store 0[/FONT]

---

### Post by dfreer on 2007-07-26
also, it has been noted that zsnes in general has scratchy sound, this can be fixed in several ways. You can use 1.51 with libao support, this works for me. 
OR You can install the libsdl1.2debian-oss library, this should help especially if you are running zsnes 1.42 (the only zsnes in the official repositories):
[libsdl1.2debian-oss]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libsdl1.2debian-oss&searchon=names&subword=1&version=all&release=all")

Sometimes, with either option increasing the sample rate to 48000hz will help improve sound quality. Of course if the problem lies within your sound card/drivers, the above will probably not help you.
This thread might ne of use:
[http://ubuntuforums.org/showthread.php?t=480988&highlight=zsnes](http://ubuntuforums.org/showthread.php?t=480988&highlight=zsnes)

---

### Post by Hybrid86 on 2007-07-26
> **JPorter said:**
> When you say "scratchy", do you mean that it's distorted?

Your PCM volume may be too high, and as a result there's a gain distortion problem with the sound card's output stage.


To check, go to the terminal and type [FONT="Courier New"]alsamixer[/FONT]

Use the left/right arrows to go to each channel, up/down to increase or decrease the volume.  Set the PCM volume to 0.00 gain.

Hit the Q key to exit.


If you want to save this so it persists through reboot as the "default", type the following at the terminal prompt:

[FONT="Courier New"]sudo alsactl store 0[/FONT]
Lowed the gain to zero, but the problem persists. As for "alsa-oss", is there anything more I'd have to do once I installed it?

---

