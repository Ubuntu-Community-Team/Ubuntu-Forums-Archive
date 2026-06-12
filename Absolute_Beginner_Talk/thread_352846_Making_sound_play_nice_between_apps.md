---
title: "Making sound play nice between apps"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by jaytek13 on 2007-02-03
Okay, so I've configured Gnome to use alsa and all that, but the sound still doesn't work between applications. If I start WoW, the sound will work fine, but no other apps are allowed to play sound while it is running. To get another app to have sound, I have to restart the sound server completely. 


How would I go about fixing this? I'd like to be able to use ventrilo and WoW at the same time, or perhaps listen to music while playing WoW, or being able to watch some flash videos while I have wow minimized, and I cannot do this as it stands.

---

### Post by pseudonym on 2007-02-03
It could be that the ALSA dmix plugin (which allows more than one app to access the soundcard simultaneously), doesn't work well for your soundcard in the default configuration. To address this, you can write a [asoundrc]("http://alsa.opensrc.org/.asoundrc") file. This will not only get dmix working, but will also give you more control over your soundcard. It's not hard to do, btw - I use the excellent template available from the [MythTV]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly") website.

For more info check out the [ALSA wiki]("http://alsa.opensrc.org/Main_Page"). You could also look at the Ubuntu [Comprehensive Sound Guide]("http://www.ubuntuforums.org/showthread.php?t=205449") if you haven't already, though I think most of the solutions mentioned there don't apply to you.

HTH

---

