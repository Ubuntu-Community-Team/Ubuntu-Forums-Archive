---
title: "Desperately Seeking Sound"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-10-20
I have tried just about everything to get my sound working again. I stumbled on this wonderful guide   ([http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide))  and even this could not do it. I got to the bottom of the stack where I was manually compiling the ALSA driver and got the message 'Build of the package alsa-source failed'.

This is all very weird as my soundcard used to work and in fact it will if I regress to a previous version of the Kernel.

Thanks for reading.

---

### Post by Pumalite on 2007-10-20
Here is a list of links, but if your kernel is not picking up your card; at the end of the day you might have to reinstall:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)

If it doesn't work go to [http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage), download the
alsa-driver, lib and utils and follow the Howto at the same address and look for your driver at the Sound card matrix. Then, if needed, apply the patch and add something at the end of /etc/modprobe.d/alsa-base (sudo gedit) at described in the previous link. I do not own the same laptop but I also have got a Intel Sound Card and worked a bit to have a functioning audio.
I hope it will help you

After fiddling with the sound settings trying various suggestions in the Comprehensive Sound Problem Solutions Guide thread, I totally buggered up my sound. Oh well, a fresh install of Feisty never hurt anyone and I had my /home directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of .config file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a .asoundrc file and another similarly named file. After doing some research here about what the file is for (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

---

### Post by linuxforrealpeople on 2007-10-27
I have come to the conclusion that the only solution is a fresh install. So I am now a gutsy gibbon user.

---

### Post by Benbow on 2007-10-27
I take it that you have been into  system/preferences/sound and made a few adjustments there? I have had sound problems as well and find that this is the best way of sorting it if your sound card has worked before.
In sound preferences/devices there are probably numerous options and it is worthwhile taking the time to fiddle with them.
It has never let me down yet!

---

