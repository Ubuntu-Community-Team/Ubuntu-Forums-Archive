---
title: "sound not working"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-11-01
Hi,

I updated my ubuntu to version 7.10 and then I had no wireless working, so trying to configure it I must have done something stupid because my sound is not working anymore. I think it was after my attempts to fix wireless, but I`m not sure. It can be after updating to version 7.10.

Well, it doesnt matter, what matter is that I have to fix my sound.

Does anyone can help me?

I have, like I said before, ubuntu 7.10 in my toshiba satellite a135-s4656

Thanks

Bruno

---

### Post by Pumalite on 2007-11-01
You might be able to find your answer in all these links and tips:
sudo apt-get install linux-backports-modules-generic
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

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

