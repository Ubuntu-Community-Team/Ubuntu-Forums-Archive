---
title: "DRI in 8.04 ppc?"
date: 2008-05-31
forum: Apple Hardware Users
---

### Post by linuxuser500 on 2008-05-31
Is there any way to get dri working on ubuntu 8.04 ppc.

I cant get it to work.

I have a powerbook pismo 400mhz with no hardware upgrades except 700 m of ram and a 40G HD

---

### Post by frog_pilot on 2008-05-31
Usually its working by default, if the machine is capable.

(If you use gnome) Look at "System" > "Settings" > "Appearance" Tab "Desktop Effects"

---

### Post by mchladek on 2008-05-31
What do you get when you run the following?
```
glxinfo | grep "direct rendering"
```
Do you have a Radeon Mobility chip in that PowerBook?  If you do, you have direct rendering enabled, and are trying to get desktop effects to work, then check out [this thread]("http://ubuntuforums.org/showthread.php?t=764633").

Compiz-fusion runs a check to see if you have a mobility graphics chip.  If you do, compiz won't load.  You have to disable that check.  That's what the thread I linked to above explains how to do.

---

### Post by linuxuser500 on 2008-05-31
glxinfo returns that I have no direct rendering
My computer has a ati rage128 chip in it.
I tried several xorg.confs from people that have it working on powerbook pismos and nothing seems to work...

I know  the card is capable bacause I have 2 rage128 cards in pcs running ubuntu 8.04 and they work fine

I am running osx right now but i will post my xorg.conf if anyone needs it

---

### Post by stream303 on 2008-05-31
It looks like some have been successful with dri by dropping their default bit depth back from 24 to 16 bits:

[http://ubuntuforums.org/showthread.php?t=3723](http://ubuntuforums.org/showthread.php?t=3723)

I wondered if this was still the case with Hardy - might be interesting to try...

---

### Post by linuxuser500 on 2008-05-31
thanks for pointing me in the right direction...  I dont know how i missed that other thread while searching.

---

