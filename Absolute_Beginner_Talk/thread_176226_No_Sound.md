---
title: "No Sound"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by crimsontide on 2006-05-14
This morning my linux box was accidentally unplugged so I turned it back on and now I have no sound. I have rebooted many times since and still no sound. Beep Media Player was the only application I had running. Is there a way I can get my sound back ?   
 
Thnx in advance

---

### Post by therunnyman on 2006-05-14
Bummer.

Check a couple things.  First, launch a terminal and type "alsamixer" (withut quotes).  In the quasi-GUI that pops up, make sure your sound device is 1) appearing and 2) has volume where you want it (you adjust the sliders with "Q," "W," and "E" for increase, and "Z," "X," and "C" for decrease).  Second, since there was an unplugging involved, make sure your speakers are plugged in and armed, and connected to your soundcard.

If that doesn't work, tell us what happened when you checked all that stuff.

therunnyman

---

### Post by crimsontide on 2006-05-14
I tried alsamixer and my sound device is appearing and the volume is where I want it. Everything seems to be plugged in as it should be. I even made sure the volume was'nt muted. Any ideas?

---

### Post by therunnyman on 2006-05-14
Let me think here...

Okay, I'm not all that familiar with Beep (I hear it's cool, but I like xmms myself), but I suspect some settings within might've gone funny.  In xmms, you have to specify a sound device...I wonder, is there something similar in Beep?  See, here I've got two sound devices, and after a malfunction, everything returns to the default sound device (a device I hate, and I don't know why it's in my machine).  I have to go in and correct everything from the default sound device in Preferences-->Sound to xmms to Apps-->Volume control-->File-->Select device.

Maybe a reinstall if all else fails?  Could be some lib or other got corrupted.

therunnyman

---

### Post by crimsontide on 2006-05-15
I have sound now, I just had to reinstall my sound card. I hope I don't have to do this every time. Thanx for all your help therunnyman.

---

