---
title: "[SOLVED] sound is gone"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2008-02-23
my dad's gutsy machine worked fine playing sound for a long time.  it is great having him use linux because he is one of the people who think they won a laptop and click on the flashing ads.  he will have a dozon malware-looking .exe programs on his desktop that he downloaded and can't figure out why he can't get the new screensavers from them (although now he likes the ant with the flashlight).  basically, he has no idea what he's doing but is generally destructive towards software, and ubuntu is good for him because he likes it.  

anyway since the inital installation, he has had sound, but for seemingly no reason it has stopped.  it uses alsa and the devices act like they think they are playing, but clearly is not.  speakers are on and in but not working.

lspci says:
00:1f.5 Multimedia audio controller:intel corporation 821801aa AC'97 audio controller (rev 02)

alsamixer brings up a pretty little mixer app, but still no sound love.

i am considering reinstalling but if i could find another way, i would appriciate it.

---

### Post by richaoj on 2008-02-24
i know this suggestion may sound silly, but the simplelest things will get us.  

have you made sure that the mute button is not clicked?

---

### Post by CRCarl on 2008-02-24
This has happened to me before - 
   The first thing I would check is that your Dad didn't change something weird. Right click on the speaker icon in the system tray and click "Open volume control". Make sure all the outputs are maxed out, then click "File -> Change Device". For every device make sure that all of the outputs are maxed out. 

   I'd also check the hardware (kicked out a plug?). 

   If that doesn't work let us know.

C

---

### Post by nonewmsgs on 2008-02-24
apparantly PCM was muted.  (wtf is PCM???)

thanks guys. i tried so many other things and couldn't figure it out.

---

