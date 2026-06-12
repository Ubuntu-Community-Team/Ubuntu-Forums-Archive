---
title: "CD-audio disc with 1 big track into many smaller mp3 files"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-06-16
I have a regular CD-audio disc (non-digital format). Everything is in one big track. I want to "chop" it up into different tracks. 
When I put in my CD into the drive, Sound Juicer pops up.

Is there a way to do the making of tracks before the extract If I first extract the big 70 minute track as 1 mp3 file and then later try to split that mp3 file into smaller mp3s would the sound quality go lower if I re-save?

What programs do you recommend to split up one audio file (whether a non-digital or a digital) into smaller mp3 files?


Thanks

---

### Post by benerivo on 2007-06-16
Audacity is very good. You can cut, copy, paste sections of an audio file quite easily. It's available through synaptic.

---

### Post by hanzj on 2007-06-16
I have Audacity installed. When do I use Audacity? While the audio CD is still in the drive, before the extraction? Or after?

Thanks, Bene

---

### Post by benerivo on 2007-06-17
Use sound juicer to extract the CD as a .wav file so that you don't lose any quality. The use synaptic to install lame, which you will need for mp3 encoding. Then open this file in Audacity. The track be displayed visually as a waveform, and you be able to see when one track ends and another begins. Using the mouse, select the part of the waveform you want to extract to a mp3. Go to Edit>Preferences, from the main menu, then File formats tab, and click the 'Find Library' button. Change the view setting at the bottom of this new window from 'Only libmp3lame.so' to 'All files', and navigate to the /usr/lib folder. Choose libmp3lame.so.0 and ignoer error message. Back on the main Audacity window choose File>Export selection as mp3...

---

### Post by hanzj on 2007-06-17
> **benerivo said:**
> Use sound juicer to extract the CD as a .wav file so that you don't lose any quality. 

Will WAV not  lose any quality because it's LOSSLESS? If so, then can one also choose the other LOSSLESS option in the list: CD Quality, Lossless, Flac Audio?

Thanks!

JC

---

### Post by benerivo on 2007-06-17
WAV is lossless, and in this case you need to use wav as it the only losless format that Audacity will read (it won't read FLAC files). You could export to  a high quality ogg or mp3 file andl not lose anything audible, but I would just go with wav as an intermediary format, and end up with either ogg or mp3 tracks.

---

