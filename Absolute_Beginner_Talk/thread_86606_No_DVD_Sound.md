---
title: "No DVD Sound"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by aerowrestlerisu on 2005-11-05
Hi, I am relatively new to linux and I am having a problem getting any dvd I put in to play sound. I have the video running just fine on both xine and vlc, but I get no audio.  My system audio does work, so I don't think that is the problem. I am not sure if I am just missing some codecs or something like that. Any help would be appreciated.

---

### Post by John.Michael.Kane on 2005-11-05
You may have to adjust the mixer from oss to alsa.. You could try this guide [http://www.ubuntuforums.org/showthread.php?t=27186&highlight=alsa](http://www.ubuntuforums.org/showthread.php?t=27186&highlight=alsa) i have had good out comes from it on my machine even with one sound card. 

please post back if issues still are there..

---

### Post by thinhlegolas on 2005-11-06
When you play the DVD, make sure no other programs like xmms or realplayer are running

---

### Post by kori.mendocino on 2005-11-06
most probably, your video players aren't set up to use the proper sound server (which would be esd by default in ubuntu).

vlc with esd
you'll need to $sudo apt-get install vlc-plugin-esd, and then, in vlc's preferences (tick 'advanced options' in the lower right corner), go to audio > output modules and choose 'EsounD audio output' from the dropdown menu.

gxine with esd
go to preferences. in the first tab, gui, you'll have to choose the experience level. choose at least the 'advanced' level, and go to the audio tab. there you have another dropdown menu, choose 'esd'

---

### Post by aerowrestlerisu on 2005-11-08
Thanks alot, that worked.

---

