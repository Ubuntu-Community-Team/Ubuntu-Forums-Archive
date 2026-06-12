---
title: "No sound on dual G4, video and modules question"
date: 2005-05-18
forum: Apple PPC Users
---

### Post by dimoni on 2005-05-18
I have installed Ubuntu-Hoary (5.4) in my dual G4 (867MHz and 512MB Ram) and can't get any sound. Nor at startup nor playing mp3 or cds. Either with alsa, sox, totem.... 
I have run the alsa speaker-test and it plays a very short impulsive sound on the correct frequency (i.e speaker-test -r 44100 -f 440, plays an A4 'tick') but that's all. I can't get a stable tone. Dont' know if this is related to, but I just explain what I've tried.
I have made sure that sound is disable at start-up. Anyway, I still don't get any sound. I didn't get any sound before, but I know that enabling sound at start-up keeps the sound device busy, so that's why I disable it.
I am not trying to get my audio(pro) soundcards to work( audiomedia and waveterminal 192X) cause there are no alsa drivers for it, but at least I'd like to have the basic/standard soundcard to work. 
I have other problems/questions also: 
I'd like to have my apple pro keyboard fully working. Meaning this, that I'd like to have the eject key, volume up/down key and mute keys working as well as screen brightness up/down ones. I have tried to do that through Preferences > keyboard shortcuts. Although I could map the eject function, volume up/down and so on to any key( F1,F2 whatsoever), but the actual ones (eject button, etc). So it seems that ubuntu can't understand/recognise those few extra keys. I have configured xorg to use either oldmacintosh or macintosh with no improvements.
More annoyances:
I have a NVIDIA GeForce video card, which at the moment is working, but I notice that when I move windows or scroll up/down the performance is worse than in other linux boxes I have (normally those have ATI video cards). I have tried to reconfigure xorg but the driver nvidia doesn't show up. Thus at the moment it is configure as using the nv driver.
In order to solve such problem I have tried to apply the nvidia-kernel patch through module-assistant with no success. Also no success, and this is a different problem, on applying realtime-lsm or alsa-modules.
My screen is an Apple Studio Display (old second-hand one). In Mac OS X the only way to change the screen v/h positions with such a display is through the preferences panel. In Ubuntu-Hoary, the screen seems to be shifted to the right ( to the point where I hardly see the clock last digit). How could I change the vertical/horizontal position of my screen. If I am not wrong xorg only configures vertical/horizontal refreshing rates but not positions.


Any help will be much appreciated

---

### Post by chrigl on 2005-05-30
Right-click the volume control and enter the mixer (I'm using the german version but it's the second item from top) check if anything is muted. For inproving the sound quality also regulate the PCM.

---

