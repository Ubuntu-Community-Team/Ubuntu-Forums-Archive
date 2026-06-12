---
title: "Logitech 5.1 Speakers"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by proventech on 2006-01-06
Anyone know how to enable 5.1 sound?  I have Logitech X-530 speakers and only 2 are producing sound.

---

### Post by s3a on 2007-12-09
I have the same problem!

---

### Post by mcduck on 2007-12-09
Have you tried with some audio source that actually has a real 5.1 sound, like a DVD movie?

---

### Post by dhobbs on 2007-12-09
First you should make sure that your sound card is being detected properly as being capable of 5.1 sound.  If it is then you can open the volume control by right clicking on the volume panel applet and then adjust the controls to your liking.

I have a Sound Blaster Live! that took a little bit of tweaking to get the surround to sound the way I wanted it but now it sounds great.

---

### Post by Mramius on 2007-12-09
How do I ensure that my sound card is being detected properly as being capable of 5.1?

---

### Post by Mramius on 2007-12-09
Anyone?  Please?  My sound is horrible! :guitar:

---

### Post by s3a on 2007-12-09
My sound card is definitely capable of 5.1 and probably 7.1 (but I'm not sure so don't take my word for it)...I experienced surround sound on this exact computer with the exact same hardware, except I was running Windows XP Professional (32-bit)...

Please help me so that I can enjoy the Half-Life series as well as DVD movies during my christmas break and more importantly my summer break (but by then I'll probably have a quad core with 4 gb ram and a 8800 GT 320 MB if the prices are right :D).

---

### Post by dhobbs on 2007-12-10
First check the driver that's being used.  System >> Preferences >> Sound.  You should see the default mixer track.  That should say ALSA (Advanced Linux Sound Architecture).  If it doesn't you should see if you can select that driver as ALSA allows multiple sound streams, whereas OSS (Open Sound System) only allows one application to access the sound system.

If you are using ALSA then you need to go to the Volume Control which can be accessed by right clicking on the volume applet in the notification area on the Gnome panel.  Open the Volume Control and play around with the settings in there.  If you don't have very many volume controls listed you can add more by going to Edit >> Preferences.

Other than that I don't know what to tell you.  I had a difficult time getting my Sound Blaster Live! to work, but that was nearly 3 years ago (the emu10k1 was brand new).

If this doesn't work than please list your audio driver reported by lspci.

---

