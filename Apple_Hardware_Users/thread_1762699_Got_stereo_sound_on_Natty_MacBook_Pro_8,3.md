---
title: "Got stereo sound on Natty MacBook Pro 8,3"
date: 2011-05-19
forum: Apple Hardware Users
---

### Post by 00000 on 2011-05-19
I have a MacBook Pro 8,3 w/ Natty installed on it and noticed on the wiki ([https://help.ubuntu.com/community/MacBookPro8-1/Natty#Sound](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Sound)) it says sound only comes out of the right speaker...  I just want to share that I got stereo sound on my machine by adding `options snd-hda-intel model=mbp55' to the end of `/etc/modprobe.d/alsa-base.conf' and rebooting.  I didn't see a solution anywhere else.

I haven't done extensive testing, I just know that now I have sound coming out both speakers (and headphone speakers) at balanced volume levels.  I hope this helps someone.

---

### Post by heathman001 on 2011-05-19
Great post! I was able to get stereo audio working on my 8,3 MBP (both internal and headphones) a different way:

1. Install gnome-alsamixer 
```
sudo apt-get install gnome-alsamixer
```
2. Unmute Front Sp and drag the level all the way up
3. Check the box to include Surround Speaker and drag the level all the way up
4. Go into the Ubuntu's Sound Settings. On the hardware tab, select the Internal Audio device. At the bottom, specify the profile "Analog Stereo Duplex". 

There are a couple of profiles that seem to work, however, Analog Stereo Duplex was the only profile that allowed me to also use the internal microphone. I have yet to get an external microphone working.

I'm curious - have you had any success with microphones, internal or external?

---

### Post by 00000 on 2011-05-22
I should have mentioned that I did fiddle with the alsamixer a bit...  Stereo sound's been working without a glitch for two days now.  I'll check out external mic and see what happens.

---

