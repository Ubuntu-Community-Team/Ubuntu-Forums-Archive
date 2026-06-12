---
title: "Problems, not sure in where"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by macg.dev.null on 2007-09-28
Ok, this has been something of a head case for me the last couple days.

First a description of the hardware I am running:

Dell Dimension C521 desktop
Video Card: ATI Radeon x1600 Pro 256mb
Ram: 1024mb

I'm making this post from work so unfortunately I'm unable at this time to post logs of my xorg.conf file.

Live CD worked like a charm, partitioned the HDD and OS installed.
I tried all manner of options and following all guides from this forum along with the ATI wiki Linux forum. Everytime that the restricted drivers, a manual driver install or Envy were used to install the drivers I would get a black screen when GDM would attempt to load.

At this time I got fairly proficient with the command sudo dpkg-reconfigure xserver-xorg.

So everytime I would reset the xorg.conf file to run using the standard VESA drivers. Eventually however one method or another I'm not sure which or if it was a combination of the different methods being tried, the ATI drivers were eventually registered and GDM booted.

Running the xlgfinfo (spellings off here, I'm tired) command returned the desired result, ATI was infact spat back out. Direct3D and OpenGL were working. Notice the past tense.

I thought to myself, great on to the next headache.

sudo apt-get install wine installed wine. Installed fine.

Installed WoW, unpatched, patching coming later when I have time. After 5 disc install completed, rebooted machine.

Here's where it gets interesting, GDM will not engage anymore. Something about "Trying to continue from something or other"

I know I'm not being very helpful, but I havent had time to play with it before heading to work. Any general ideas? I'll be making a more documented post with exact error messages in the morning when I get home, but for the time being just wanted some food for thought.

Btw, this is my first forray into Linux.

---

### Post by macg.dev.null on 2007-09-28
Bump..

---

### Post by nowshining on 2007-09-28
wine is in Development still  - :) some things may or may not run on it  right now and some require extra dlls files ur windows windoe folder is located in ur home directory .wine and is hidden by default - extra info.

winehq.com
edit: database is located here [http://appdb.winehq.org/appview.php?appId=31](http://appdb.winehq.org/appview.php?appId=31)
is the official site. :) they have been keeping track of what games work and what doesn't.

---

