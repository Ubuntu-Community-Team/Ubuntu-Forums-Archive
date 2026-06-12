---
title: "some general advice about settings in fiesty"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-22
hello, firstly im finding fiesty alot easier to deal with than edgy, which is good.
now the first thing is that my monitor runs best at a resolution of 1280x800 @ 75 mhz refresh rate, but when i start ubuntu the resolution is set at 1024 x 768 and the resolution is set to auto (this is on an nvidia 7 series agp card, with the latest drivers installed) so everytime i load ubuntu up i have to change the resolution etc etc, so how can i get it to start up at this resolution ? ive tried some commands i had for re-configuring the xserver and so on, but they dont work (maybe different commands with fiesty from what they were in edgy ?) so any help with this would be very appreciated.
the other thing is that although i set beryl up to load at start up it doesnt, so any ideas on this would also be appreciated.
cheers.

---

### Post by Kobalt on 2007-05-22
You can edit manually your xorg.conf file and remove any other resolution appart from the one you want. 
```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by southernman on 2007-05-22
If your using system > preferences > screen resolution - when you change to the res of choice it'll give you a box to tick at the bottom of dialogue box to make it the default...

If you've tried that... dunno. *shrugs*

---

### Post by ugm6hr on 2007-05-22
If 1280x800 doesn't appear in the GUI settings, then edit xorg.conf manually, as suggested.  The Monitor and Screen sections are most important. 

Just make sure **"1280x800"** appears first after Mode in every entry in Section Screen / Subsection Display.  

The HorizSync/VertRefresh in Section Monitor should match whatever it says in the monitor manual (presumably you meant 75Hz vertical refresh).  I don't think there's any good reason to have a range of values if you know what the exact ideals are for your hardware - unless someone knows better?

---

### Post by techno-mole on 2007-05-23
cheers, tried setting the default resolution to what i wanted using - system--preferences--screen reolution, but it didnt worked, ive just edited the xorg.conf file so i shall give that a bash.
cheers for the help.

---

### Post by techno-mole on 2007-05-23
ok managed to get my screen resolution to what i want it with out having to keep adjusting the nvidia settings .
so now a question, i had trouble with edgy playing embeded files, so stuff like film trailers and what not, is this still the case in fiesty ? and if so whats the best way to sort it ?
the other thing is that i could never install wine with edgy, it just locked the system up, and ive tried to install it under fiesty and the same thing happens, is there a way to fix it ?
cheers in advance for any help given.

---

### Post by Nythain on 2007-05-23
sudo dpkg-reconfigure -phigh xserver-xorg

select the correct driver and highest resolution, or res you want to run at

---

### Post by ugm6hr on 2007-05-23
> **techno-mole said:**
> 
so now a question, i had trouble with edgy playing embeded files, so stuff like film trailers and what not, is this still the case in fiesty ? and if so whats the best way to sort it ?


Unfortunately, Ubuntu doesn't include a lot of media codecs (to play e.g. realplayer, quicktime, flash etc), so they have to be installed afterwards.  It is pretty easy though - this is a good place to start:
[https://help.ubuntu.com/7.04/musicvideophotos/C/onlinemedia.html](https://help.ubuntu.com/7.04/musicvideophotos/C/onlinemedia.html)
The other thing I find useful is the Firefox media player connectivity plugin - available from the firefox addons webpage - just search for it.
I personally use VLC for most file types and realplayer for realmedia.

---

### Post by techno-mole on 2007-05-25
cheers for the help, most useful

---

