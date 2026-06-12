---
title: "HOW TO: fix no sound problem in flash"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Afkpuz on 2008-02-29
I came across a different and easier fix.  It seems like my problems stemmed from multiple sound card.  Flash was use the ALSA default card, even though I had changed the choice of default cards in System>Preferences>Sounds


So, make sure your correct sound card is set as default



This lists your detected sound cards
```
asoundconf list 
```

Note the name of the correct sound card. Then,

```
asoundconf set-default-card cardname 
```
Where "cardname" is replaced with your card's name.  


This solution worked on a fresh install for me and required no additional packages to be installed.  Hope this helps more than the last method!



********Edit*********old stuff***********

There seem to be several fixes out there.  Here is one that worked for me on a fresh install

*EDIT* If you have tried to install pulse audio, then gone back to alsa, expect this not to work.  Pulseaudio doesn't like to go away.  So, please note that this is based on a FRESH INSTALL

```
sudo apt-get install alsa-oss
```


Change the command used to open firefox.


Rightclick on "Applications" =>Edit Menus

Select "Internet" on the left side.  Then, right click on firefox.  Select "Properties"

Change the command to:
```
aoss firefox %u
```



Hope this helps.

**************Edit***************old stuff******************

---

### Post by jan quark on 2008-02-29
nice that it worked for you but please post guides and tutorial in the appropriate forum section 

tutorials and tips

thank you

---

### Post by Afkpuz on 2008-02-29
Opps.  can one of you awesome mods move this post for me?

---

### Post by tekDragon on 2008-03-08
Tried just about every fix I could and this is what finally ended up working for me.

Many many thanks.

---

### Post by himynameiskevin on 2008-03-09
didn't work for me. this problem just randomly came up yesterday, seemingly out of nowhere. it's getting really frustrating. sound doesn't work in epiphany either

---

### Post by himynameiskevin on 2008-03-09
okay, this fixed it for me..

> **TaTaE said:**
> Maybe those who get this error mesage have pulseaudio installed. Pulseaudio is really great , BUT is not implemented on some games and other programs. So, if you are in games, you better get rid of pulseaudio, by searching "pulse" in synpatic and purging it all. Than, you will have ALSA audio left, which is default in Gutsy. For complete uninstalling , you must do "sudo aptitude purge libpulse" and install libesd-alsa.
     Some report that "asoundconf reset-default-card" did the trick for them.
:guitar:

---

