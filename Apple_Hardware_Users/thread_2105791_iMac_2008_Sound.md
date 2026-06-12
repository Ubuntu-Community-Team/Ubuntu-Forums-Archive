---
title: "iMac 2008 Sound"
date: 2013-01-17
forum: Apple Hardware Users
---

### Post by indigosunrise on 2013-01-17
Hey people. Just curious as to whether anybody running Ubuntu on older iMac's have been able to get sound working???

Upon installing 12.04 there was no sound at all, so edited modprobe.d/options and included something along the lines of "snd-hda-intel model=imac24" which has gotten some sound to play out of the right speaker but not the left.

Would like to get this working because I use the iMac partly as a bedroom tv so sound is important.

Thanks in advance...

---

### Post by iMac71 on 2013-01-17
on my iMac 7,1 (mid 2007) I haven't ever got any problem with sound.
Did you do the sound test in System settings before of modifying modprobe.d options? If so, what has the result been? Did you hear any sound from the left speaker?

---

### Post by indigosunrise on 2013-01-18
I did go into sound settings and did the sound test before I altered modprobe options and there was no sound coming out of left or right. So I followed the instructions on an intel imac ubuntu installation guide which suggested the alteration I made. 

If you're talking about a different test, like in the extensive system diagnostic tests then no I didn't.

There was also another page I saw that got me to alter the same file with something different to imac24 but there was no difference in the result.

---

### Post by indigosunrise on 2013-01-18
Oh thought I'd mention that I tried from another a thread that I tried lenovo-sky in modprobe like suggested in another thread on these forums and same result.

---

### Post by indigosunrise on 2013-01-18
Okay. A quick update - I reinstalled a bunch of alsa module and driver packs and now I manage to get sound when I boot up into the login screen, but when I log into my window manager I get nothing.

According to alsamixer it is not muted, and none of the settings under sound and hardware work successfully when I test the speakers.

I'm sure from here this is an easy fix but I'm struggling to work out the connection and how to proceed.

---

### Post by indigosunrise on 2013-01-20
None of the modprobe edits produced more than crappy and weak mono sound. I had to purge and reinstall every alsa and pulseaudio specific package, reinstall the pulseaudio and alsa kernel\modules and the hda intel drivers. Couple of other things I tinkered with that might have had an impact, but if anybody needs those details down the track feel free to PM.

---

