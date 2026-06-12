---
title: "Microphone not working on Ubuntu Eee PC"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by anotherghost on 2008-04-03
I recently installed Ubuntu on my Eee PC, and everything is working fine except I can't get the internal mic to work.  I followed the instructions on [this page]("http://www.sampletheweb.com/2007/12/11/ubuntu-on-the-asus-eee-pc-part-2-or-how-to-install-ubuntu-on-the-eees-internal-drive/") to install it.  It told me along the way to add this line...
```
options snd-hda-intel model=3stack-dig
```
...to the beginning of the options section in /etc/modprobe.d/alsa-base.  So, I did that, and it still doesn't work, either in Sound Recorder or in Skype.

Help a novice out? :)

---

### Post by annda on 2008-04-03
sorry if the question sounds stupid but have you checked all the sound settings? is mic capture enabled?

---

### Post by anotherghost on 2008-04-03
Well :P As I said I'm a novice, so I'm not sure.  I went to System->Preferences->Sound and it has a part called "Sound Capture" that is set to ALSA (which, when I try to click test, gives me an error).  I don't see any option called mic capture though, is that somewhere else?

---

### Post by meborc on 2008-04-03
try alsamixer from the terminal... try to unmute everything with a "m" key

---

### Post by anotherghost on 2008-04-03
Well I tried alsamixer and unmuted everything, and have fooled around with that for a bit, but it still won't work at all.  I'm at my wits end, I'm really not sure what to do.  Anybody have any ideas?

---

### Post by rykel on 2008-06-07
Me too... my microphone was borked after applying the RiceyTweak.sh and Skype now sounds only on one side of my earphones.

---

### Post by rykel on 2008-06-07
I reapplied the eeeTweak.sh from eeeuser.com and now sound is back to normal. Skype has become "stereo" again, and unmuting microphone causes an echo of all things going into the microphone, such the click-clark of the keyboard keys.

However, the actual recordings did NOT show that the microphone is working - voice just comes out as static.

Still awaiting a solution... thanks!!

---

### Post by golovan on 2008-06-19
I'm running Ubuntu eee (gold) and have run the ubuntutweeek-script to fix sound. Sound seems too work now, but I too had problems with the microphone in skype. Could hear myself (echo too...) but others couldn't. Fixed it like this:

Right click on speaker icon 
> "open volume control" 
> "Edit - Preferences" 
> check/enable "input source" (and "Front mic" if it's not enabled) and close that window 
> go to tab "options" 
> choose "Front mic" 
> go to tab "Playback" and verify that the faders for "Front mic" is set correctly and not muted.

Now Skype is working (and the echo is gone)

---

