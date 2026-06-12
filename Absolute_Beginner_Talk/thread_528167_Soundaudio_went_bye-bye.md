---
title: "Sound/audio went bye-bye"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by CocheseUGA on 2007-08-17
Sometime, somewhere, audio went out. I couldn't tell you when, because I never use it on this machine. BIOS beep still works, but nothing in the login/splash screens, and nothing from my new CDROM. There is no BIOS setting to enable or disable onboard audio, so I'm sure that's not it.

How else can I troubleshoot this? I'm totally out of ideas.

---

### Post by r4ik on 2007-08-17
Try,

[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !

---

### Post by Vanish00 on 2007-08-17
I have the same problem too my sound just vanished when I was trying to get my mplayer to work.  I followed the link above but on step 3 I can't find any drives at this site that the guide linked for us.   [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

---

### Post by r4ik on 2007-08-17
Seems they have changed it maybe,

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

helps,

Look for " Is my soundcard supported?"

Good luck !

---

### Post by Vanish00 on 2007-08-17
I found my driver to be snd-ca0106

In the guide it calls for
"sudo modprobe snd-ca0106  "

Once i type that the guide says to press TAB then ENTER to get a list of modules but I dont get a list.  I'm just sitting at a new prompt line.

---

### Post by CocheseUGA on 2007-08-17
It's odd that it would work, then it wouldn't. Not when I haven't touched anything related to it.

I'll check it out next time I boot my laptop. Thanks though.

---

### Post by r4ik on 2007-08-17
Looks to me you have to build fresh kernel it follow these steps

Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot

Or have look at,

[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)

If anybody has an more easy solution please be my guest. :)

---

### Post by Vanish00 on 2007-08-17
Anybody know where i can find the alsa-driver package for CA0106 soundcard?  It's not at this site ([http://www.alsa-project.org](http://www.alsa-project.org))  that the guide mentions.

---

### Post by Vanish00 on 2007-08-18
I just got ALSA drivers from a *fresh* kernel and still no sound...*sigh*  I just had sound for about a month or 2 and just disappeared today.  I wish my problem was mute but I've check Alsamixer and its maxed out in volume.  Anything that has a volume control I have to the max.  Anybody have any ideas, i'm sure it's one little thing i'm over looking.

---

### Post by r4ik on 2007-08-18
I googled for "alsa-driver package for CA0106 soundcard" and it does not looks too good.
Seems to be a pain in the *** that Soundblaster card.
My advice go buy another card.

---

### Post by Vanish00 on 2007-08-18
Any recommendations for a good sound card?

---

### Post by r4ik on 2007-08-18
Have a look at,

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

Hope it helps.

---

### Post by Vanish00 on 2007-08-18
That chart really needs to updated, last update on it was January 8, 2007.  r4ik, thanks for the help you've been really helpful.  This is looking more and more like a lost cause.  Looks like back to windows for me till I'm ready to deal with this again.  r4ik, thanks for the help!

---

### Post by r4ik on 2007-08-18
Sorry i could not help this is as close as i could get,

[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)

Good luck !

---

