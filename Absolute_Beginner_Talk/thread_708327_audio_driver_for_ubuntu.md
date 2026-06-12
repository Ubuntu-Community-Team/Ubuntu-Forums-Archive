---
title: "audio driver for ubuntu"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-02-26
i am looking for a suitable audio driver for realtek ac'97 audio on my system that will work with Ubuntu 7.10... does anyone know where i can find one?  i am trying get the best sound quality possible out of my audio apps (VNC for example) in Ubuntu, but they don't sound nearly as good as what i am used to hearing from Windows under WMP.  thanks.

---

### Post by sayakb on 2008-02-26
> **Matt26 said:**
> i am looking for a suitable audio driver for realtek ac'97 audio on my system that will work with Ubuntu 7.10... does anyone know where i can find one?  i am trying get the best sound quality possible out of my audio apps (VNC for example) in Ubuntu, but they don't sound nearly as good as what i am used to hearing from Windows under WMP.  thanks.

You do not need separate audio driver for your device. 
Go to System -> Preferences -> Sound
For Sound events and Music, select ALSA from the menu.

Also, Double-click on the Volume Icon in the notification area, goto File -> Change Device and select ALSA Mixer.

---

### Post by Matt26 on 2008-02-26
thanks for the suggestion- if i remember correctly i do have the ALSA option selected under Sound preferences, but i still have sound quality issues... is there any way to improve it so that it sounds like what i hear under windows xp?

---

### Post by sayakb on 2008-02-26
> **Matt26 said:**
> thanks for the suggestion- if i remember correctly i do have the ALSA option selected under Sound preferences, but i still have sound quality issues... is there any way to improve it so that it sounds like what i hear under windows xp?

If you want reverb, virtual surround, then I don't really know any app providing that (others may help you in that context). You may though try Amarok. I use Banshee music player, just keep the PCM bar a little low and my speaker's native controls high to get clearer sound.

---

