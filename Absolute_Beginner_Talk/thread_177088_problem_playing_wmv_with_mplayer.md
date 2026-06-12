---
title: "problem playing wmv with mplayer"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by shurguywutt on 2006-05-15
when I play wmvs with mplayer, I keep getting a reoccuring message that says "ALSA-Control: Unable to find simple control 'PCM',0"  The sound and the video plays, but this message just keeps coming up.  Any suggestions?

---

### Post by shurguywutt on 2006-05-15
I also get this message when I try to play it in kaffeine "ALSA device "default" is already in use by another program."


I am running breezy 5.10 and I have a geforce 5200 128 mb card.

---

### Post by Sef on 2006-05-15
Have you downloaded the codecs?

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

Is what you playing encoded? that may be the problem.  You may not be able to play it if it is encoded.

---

### Post by shurguywutt on 2006-05-15
yes I have.

---

### Post by nalmeth on 2006-05-15
PCM.. hmm

does this happen if you use totem too?

do you have a music player running the background too?

---

### Post by shurguywutt on 2006-05-15
A variation of it happens in both totem and in mplayer, i have all the codecs, and i dont have any program except gaim running in the backround.

---

### Post by timon_tg on 2006-11-14
I have the same problem when I play with mplayer, I keep getting a reoccuring message that says "ALSA-Control: Unable to find simple control 'PCM',0" The sound and the video plays, but this message just keeps coming up. Any suggestions?

Creative Live 5.1 24bit

---

### Post by hernyman on 2006-11-28
I've found the solution for this problem:

If you have a SB Live 24-bit and mplayer gives the "Unable to find..." error, do this:

* Go to Preferences -> Audio tab
* Select Alsa and click "Configure Driver"
* Set "Device" and "Mixer" to default
* Write "Analog Front,0" into Mixer Channel.
* Press OK on both windows.

It worked for me!

---

