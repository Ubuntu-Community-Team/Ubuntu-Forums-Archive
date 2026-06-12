---
title: "Sound problem with Audigy 2"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by rorschach on 2007-03-30
I just installed Feisty, and have a strange sound problem. I have none immediately after install.
I have on-board sound, and an add-on, audigy 2 card, it appears that I cannot make the audigy my default, though it is being recognized by ubuntu.

I followed one of the guides I found linked in the forums ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting))
Here's what happened:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils 

this, as the guide suggested, also removed gdm and ubuntu-desktop

rebooted into command line login.
sudo apt-get install gdm ubuntu-desktop
startx
I have sound at this point.

Then I rebooted to test the gdm login
no soiund

I went through the purge/install again
installed only gdm this time
startx
I have sound

reboot again
no sound

It appears that gdm is killing my sound. any ideas?

---

### Post by thomas.hoyland on 2007-03-30
hey there
i too have an audigy 2 and have had no problems

i disable onboard sound in the bios as it always takes priority over addon cards.

Regards,
Tom

---

### Post by rorschach on 2007-03-31
Perfect!
That did it - thank you!

---

### Post by castronovab on 2007-04-07
> **thomas.hoyland said:**
> hey there
i too have an audigy 2 and have had no problems

i disable onboard sound in the bios as it always takes priority over addon cards.

Regards,
Tom

so how do i do that, i am having the same problem

---

