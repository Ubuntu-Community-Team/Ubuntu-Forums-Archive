---
title: "Audio Problems"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Ed933 on 2008-02-02
Hey huyz, sorry if this has already been posted, I've got a SoundBlaster Live! Value card using the kernel module emu10k1 (I loaded it using "sudo modprobe snd-emu10k1), turned ALL the settings in the mixer to MAXIMUM and did 'speaker-test' and got a faint crackle... Also, I d/led an mp3 and opened it in gxine which played through '38 seconds' of it (although the song was well over 3 minutes) in 2 seconds with no sound ?!

I'm certain the speakers are setup correctly and work fine, as they were working perfectly with playing games and DivX movies on Win2k Pro.

If this helps, I'm running Xubuntu 7.04 "Fiesty Fawn". 

Here are the rest of my system specs - 

1.3GHz P4 
128MB RDRAM
Nvidia GeForce2 MX

---

### Post by visible on 2008-02-02
[URL="http://ubuntuforums.org/showthread.php?t=205449"]http://
ubuntuforums.org/showthread.php?t=205449[/URL]
have you seen this thread maybe it will help you.  also do you have the codecs and want not installed for mp3 and the like?  google medibuntu for info on that.
by the way what is rdram?(not to sound dumb, I just never heard of it)

---

### Post by RomeReactor on 2008-02-02
Hi. To enable MP3 playback, install **xubuntu-restricted-extras**; look for it in Synaptic, or to install from the teminal:
```
sudo aptitude install xubuntu-restricted-extras
```

---

### Post by Ed933 on 2008-02-02
RDRAM is Rambus RAM...It's faster than DDR or SD...but MUCH more expensive...its not mainstream anymore...that's why it's so expensive...

So it must be a codec problem...Thnx guyz...I'll try that...can u explain the crackling sound in speaker-test? 

thanks for your reply :D

---

