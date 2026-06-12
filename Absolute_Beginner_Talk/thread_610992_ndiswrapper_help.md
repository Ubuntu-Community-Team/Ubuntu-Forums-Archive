---
title: "ndiswrapper help"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by tibby_ on 2007-11-12
So i visited the ndis wrapper and got all of the needed downloads form my bcm4318 airforce one wireless card and have them now on the desktop of my machine that is running ubuntu studio but am kind of lost as to what to do now. any help would be amazing

---

### Post by KentS on 2007-11-12
This guide might help you out:
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

---

### Post by drunkardivan on 2007-11-12
I found this [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501) thread to be quite helpful.

---

### Post by poudin on 2007-11-12
ndiswrapper -i <location_of_your_driver>/<the_driver>.inf
ndiswrapper -l

it was pretty good for the HP pavillion 1000 we used it on...just had to make sure we had the right *.inf
for the laptop..we grabbed the XP version 

we used lspci to confirm the model of the wireless network controller (ours was BG2200 Intel)


From this website
[http://www.linlap.com/wiki/Configuring+the+ndiswrapper+driver+for+wireless+controllers+without+native+Linux+drivers](http://www.linlap.com/wiki/Configuring+the+ndiswrapper+driver+for+wireless+controllers+without+native+Linux+drivers)

good luck

---

