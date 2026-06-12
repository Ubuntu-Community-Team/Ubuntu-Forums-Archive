---
title: "Sound, trackpad on new Asus 1215B"
date: 2011-10-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by landsw on 2011-10-28
Greetings, I just bought an Asus 1215B (darn good price) C50 AMD processor and immediately started playing around with linux. I've used Macs for the last 8 to 10 years and have no experience with Linux at all.

I decided to install Ubuntu and it was great, but a bit sluggish (not nearly as glacial as the Windows it came with) but certainly doable. Everything worked. The track pad would vertical and horizontal scroll, two fingers for right click, sound, etc.

I then tried Peppermint OS, Joli OS and Lubuntu. I decided to go with Lubuntu because it was the fastest.  However I have no sound - no sound icon in the panel, no sound option in system settings, and no sound to hear. 
I also installed gsynaptics and no horizontal scrolling or two finger right click. 

I tried all of them on USB first and installed Ubuntu then decided Lubuntu and installed it (not realizing the sound wasn't there). 

11.10

Any ideas?
thanks,
Rick

---

### Post by FX2908 on 2011-11-14
Free bumping because i had these sound problems too and i couldn't find a solution either...

---

### Post by Hutom on 2012-03-22
ASUS 1215b with lubuntu. Having same problem. No sound icon on the panel. Anyone?

---

### Post by Hutom on 2012-03-22
Solved it.

Seems that there are 2 audio cards - one ATI and the other Realtek. ATI card cannot be read but Realtek card can be used. So we need to switch the Realtek card as the default card to be used. 

What I did is the following-

Installed gnome-alsamixer from synaptic. 

Found that **asound.conf** file was missing in the 'etc' folder under 'File System' in 'My Computer'.

Opened a leafpad. Wrote the following in the pad:
```
defaults.clt.card 1
defaults.pcm.card 1
defaults.timer.card 1
```
Saved the file as **asound.conf** in etc folder.

And that is all. It is now working fine. :guitar:

---

