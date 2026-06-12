---
title: "[SOLVED] Fresh Gutsy and still no sound"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-11-09
Hi, does anyone with hda intel sound have sound on Gutsy, because I had with Feisty, and after updating to Gutsy I lost my sound and then after severals attempts to put sound ([likethispost]("http://ubuntuforums.org/showthread.php?t=606444"). I decided to install a fresh installation of Gusty. So I downloaded it, and then I started the live cd, and the same problem occured. But anyway I installed it from scratch. Formated the partition and all and installed. But the same problem is occuring. No sound at all. I must say that I am veeeeery disapointed with Gutsy.

Now I am typing this thread from windows :( can you believe. grrrrr

So the question is, why does gutsy dont recognize my sound?????

I have a laptop toshba a135 s4656 and like I said before the sound is hda intel sound. So does anyone can help me, if no, does anyone with the same sound chip have soung in gutsy??

Thanks.
Bruno

---

### Post by Therion on 2007-11-09
[Comprehensive Sound Problem Solutions Post]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide")

---

### Post by Rich78 on 2007-11-09
Have you tried.

sudo adduser <username> audio

Where <username> is obviously replaced with your username.

---

### Post by Pumalite on 2007-11-09
Try this:

sudo apt-get install linux-backports-modules-generic

---

### Post by Fire_Chief on 2007-11-09
This user also has a Toshiba A135  (different sub-version though) and he got sound working.
[http://ubuntuforums.org/showthread.php?t=530374&page=8]("http://ubuntuforums.org/showthread.php?t=530374&page=8")

Also look at the first page of that thread. It has a guide on debugging Intel HDA Audio.

---

### Post by Lifeless1 on 2007-11-09
I have the same problem.  I just installed Ubuntu, yet from the start, there was no sound. My sound cards (Creative Sound Blaster something or other, Riptide) show up and say that they are working and that the drivers are obviously there and working.  It seems kind of odd that a fresh install would have trouble getting the sound to work.  
      If it helps, my computer is a Compaq DeskPro Workstation with 640 megabytes of RAM, the default power supply, two hard drives (one for Windows, one for Ubuntu, although that may change soon), NVidia GeForce 6200, two network cards (one built by Linksys, the other is the default), Intel Pentium 4 processor (1.5 GHz), default motherboard, Lite-On DVDRW drive, and the default floppy drive.
:confused:

---

### Post by Pumalite on 2007-11-09
Here you have some links to check:

[http://ubuntuforums.org/showthread.php?t=604084](http://ubuntuforums.org/showthread.php?t=604084)
[http://ubuntuforums.org/showthread.php?t=569280](http://ubuntuforums.org/showthread.php?t=569280)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

---

### Post by brunoskrebs on 2007-11-09
Ohh finally thanks people:

Backports worked for me:

[link]("http://ubuntuforums.org/showthread.php?t=530374&page=8")

Thanks thanks thanks

lol

---

### Post by Lifeless1 on 2007-11-09
Thanks, the problem has been solved.:)

---

