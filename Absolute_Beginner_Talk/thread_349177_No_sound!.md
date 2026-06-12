---
title: "No sound!"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Starik on 2007-01-29
Hello,
I'm obviously new to Ubuntu and to the whole concept. The problem is that I have no sound except "log in" and "log out" drums that seems to be uncontrollable (i.e. unable to mute it or lower the volume).
I have two sound cards: external one M-Audio FireWire Solo and internal SoundBlaster Live! 24. Neither of these Ubuntu recognizes as I don't see it under SYSTEM->PREFERENCES->SOUND. I perform TEST soundcard and no results, it just testing and testing and testing....
What to do to get the sound from UBUNTU?
Thanks a lot!

---

### Post by NewOldTimer on 2007-01-29
New here, but theres more options thru volume icon{right click} on the panel, hope it gives you some help

---

### Post by BjarneJ on 2007-01-30
Check out this:

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

### Post by deadgobby on 2007-01-30
You not need to do the above link. You have 2 sound cards and Ubie see both. Now to get just the SB just working a lone. You'll need to go into your BIOS and disable the on board sound device. Reboot the system. Next is install ALSA mixer to control the volume. There is serval ALSA mixers. One is to install ALSA Gnome. That is a graphic one and can be install in Synaptic Package Mang. The other ALSA mixer can be install through Synaptic too. Or you can install through the Terminal.
sudo aptitude install alsamixer

Once installed. In the Terminal type in 
alsamixer
Use the tab and arrow keys and play with the settings.

Gobby

---

