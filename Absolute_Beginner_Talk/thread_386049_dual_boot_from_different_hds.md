---
title: "dual boot from different hds"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Cipher Short on 2007-03-16
Hello and good day. Newbie here. I have looked all over but still haven't found quite what I'm looking for. I am currently running XP (yuck) and would like to put ubuntu on my second internal hard drive and create a dual booting pc. It seems to me I should only have to format the hard drive so its empty and when I tell ubuntu to install just be sure I chose the correct hard drive. Other then choosing the wrong drive are there any other issues I should worry about concerning the integrity of the data on the other hd?

TIA- CipherShort

eMachines T3410  AMD Sempron processor 3400+   2.01 GHz  896 MB of RAM

---

### Post by oilchangeguy on 2007-03-16
the way i set it up was to put ubuntu on the master drive, and xp on the slave drive. just change the jumpers on the drives (you may have to also move the drives around so the cable will connect properly as well). do this before you install ubuntu, xp doesn't care if it's master or slave. ubuntu does. let me clarify, if you install ubuntu as either master or slave, leave it there. don't change the jumpers after, it confuses linux.

---

### Post by Griffiss on 2007-03-16
I had the same setup last friday (xp on master drive and empty 2nd drive). During the install process I selected the slave (2nd drive, logical name hdb1) for ubuntu and selected the 'erase entire disk' option. Install went smoothly and still working fine. (@oil change: what are the issues with putting ubuntu on slave? do they apply to edgy?)

As long as you don't tell it to, the install process won't touch your windows drive. It will, however, set up your dual boot automatically - it did with me anyway, running edgy:)

---

### Post by maccawolf on 2007-03-16
It does? I installed it as my internal IDE slave and it works there.

---

### Post by Cipher Short on 2007-03-17
:popcorn:  Heres to you guys for all your help. I have installed it on my second hd w/o any problems I noticed. Im so happy cuz it went to the top of the boot list so i dont have to do anything and it loads up right away :D Now to figure out the java applet and other mis. little things. I love to learn, this is so much fun :guitar:

---

### Post by wearekosh on 2007-03-17
Hi - If you want to do it from one drive - look at this :)

[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

---

