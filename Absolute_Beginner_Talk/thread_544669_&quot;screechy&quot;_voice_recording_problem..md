---
title: "&quot;screechy&quot; voice recording problem."
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Caermundh on 2007-09-06
I am using ubuntu 7.04 alternate install and im having a big problem with recording voice from a microphone in Audacity.

I can record just fine, but when I play it back, the audio is very "screechy" and metallic sounding. Its really quite unpleasant. I have tested the microphone and soundcard under windows so i know they are good. My audio voice recordings were fine under windows. i upgraded alsa to the 1.0.14 drivers and that didnt solve the problem.

how do i fix this recording problem? or alternately, since i KNOW the windows xp drivers wil work perfectly with the soundcard, is there some way to get Ubuntu to use the xp binaries?

---

### Post by annda on 2007-09-06
i don't think you can use windows sound drivers for linux.

but you can double-chceck all the alsamixer, recording, encoding etc. options. can you get a decent sound with the standard sound recorder?

and what is your sound card?

---

### Post by Caermundh on 2007-09-06
if i play with the sliders in alsamixer, i get louder or quieter recordings accordingly, but no matter what level i put the capture and microphone sliders at, it still has that annoying screech to it.

As for the sound card "lscpi | grep -i audio" returns:

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)

oh, and as for the standard sound recorder, i cant get it to play back anything i record, or maybe its just not recording it in the first place *shrug* (i have no clue what im doing with that thing)

EDIT: ok i think i just figured out what im doing with the standard recorder. it seems it only RECORDS and doesnt playback. If i save the recording and play it back in mplayer, i can hear the recording. Voice recording in the standard recorder is absolutely FINE, no screechiness at all. I guess this means the problem lies in Audacity.

---

### Post by Caermundh on 2007-09-07
bump....can anyone tell me why audacity does so poorly at recording voice? and/or how to fix it?

---

### Post by narrowhouse on 2008-02-19
Caermundh probably doesn't need this answer anymore but just in case someone reads this thread I have a possible solution. This worked for me in Gutsy.

In Audacity go to Edit --> Preferences --> Audio I/O

If Playback and Recording devices are set to OSS /dev/dsp change them to ALSA: default and you should have no more problems with the screeching metallic ring.

---

