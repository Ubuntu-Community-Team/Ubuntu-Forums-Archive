---
title: "&quot;No Screens Found&quot;"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by neologism on 2007-03-11
Ok, so i keep getting the 'no screens found' error while trying to start the xserver after a fresh install of Ubuntu 6.10.  I'm using a 20" Viewsonic lcd paired with an Nvidia 8800gtx (DVI cable).  Here's what I've tried so far:

sudo dpkg-reconfigure xserver-xorg
    -tried most options, yes/no to frame buffer, correct  vertical/horiz sinc (according to manual), resolutions, both nvidia and nv hardware at the starting select screen.

sudo apt-get update

sudo apt-get install xserver-xorg-core

sudo apt-get install nvidia-glx

startx (of course)

I think I've tried all possible combinations and orders of these commands, with no luck.  Also tried with VGA cable (thru a DVI adapter on the back of the video card).  This install was using the alternate install CD (text based installer).    Is there something Ubunutu doesn't like about lcd monitors?  Is it the new nvidia hardware?  Any help is appreciated.

ps. You'll have to talk to me like I don't know what I'm doing. I don't.  Please type any commands word for word.  thanks

Athlon64 3000+
DFI Lanparty
nvidia 8800gtx
2gb Mushkin
WD Raptor

---

### Post by matburton on 2007-03-11
What does the liveCD do?
Can you get into Gnome with that?

---

### Post by neologism on 2007-03-11
No, I can't get to Gnome with the live CD.  The graphical install method hangs also.

---

