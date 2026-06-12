---
title: "sound issue"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by audiofeen on 2008-02-17
hey guys

obviously i'm new to this :) and so happy to have an operating system that is not windows 
i have a problem with the sound on the laptop.

the driver seems to be running but no sound coming out of on board speakers or headphone jack.
i'm using a ecs laptop model: X20II1 it's running in restricted driver mode, this maybe the problem but i'm to unexperienced with linux to know would that effect it as most of the other drivers seem to be running fine. is there a help topic somewhere for sound drivers 
correct settings and so on.

i make computer music on mac most of the time so i do have a bit of experience with messing around with drivers.

any help would be much appreciated 

audiofeen

---

### Post by audiofeen on 2008-02-17
anyone?

---

### Post by jan quark on 2008-02-17
welcome to ubuntu

try these sites first and if you hit the wall ask again :)

[https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29](https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=sound&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=sound&titlesearch=Titles)

I am not that into the sound issues :)

---

### Post by audiofeen on 2008-02-17
thanks :D 
appreciate it

---

### Post by audiofeen on 2008-02-17
hey got this far (sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils) 
then when i went to re-install it just like it says in the note it could not find
it so i tried the second (sudo apt-get install gdm ubuntu-desktop) and that didn't work either

anyone know a comand to get a re-boot to a gui


here's the topic

Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

    *

      Remove these packages sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
    *

      Reinstall those same packages sudo apt-get install linux-sound-base alsa-base alsa-utils 
    *

      VERY IMPORTANT NOTE - Ubuntu (GNOME): users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following sudo apt-get install gdm ubuntu-desktop
    *

      VERY IMPORTANT NOTE - Xubuntu (XFCE): users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base. If this happens, then do the following sudo apt-get install gdm xubuntu-desktop
    *

      Reboot
    *

      At this point, try using aplay -l you should get your soundcard listed.
    *

      Success - Your soundcard is detected. Go onto the Using alsamixer section, then try playing something on your music or media player.
    *

      Failure - Your card was not detected. You should try compiling your driver, so go onto ALSA drive Compilation.

Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.

---

### Post by audiofeen on 2008-02-17
ahhhhhh i re-instaled gutsy i have a version of festy fawn downloading at the moment if i have the same problem ill try that 

found my drivers from realtek and installed them but not joy still 
i have a Realtek ALC861 sound card 

anyone any help :D

---

