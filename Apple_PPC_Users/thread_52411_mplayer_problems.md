---
title: "mplayer problems"
date: 2005-07-27
forum: Apple PPC Users
---

### Post by ssam on 2005-07-27
does mplayer work on powerpc for anyone?

it seem that the package lack the executable file.

---

### Post by craks on 2005-07-27
i have compile mplayer 1.0.7 from source and add realplayer codec. All works fine

download mplayer, [http://www1.mplayerhq.hu/](http://www1.mplayerhq.hu/)

./configure --with-reallibdir&#65309;/opt/RealPlayer/codecs/
(if your realplayer installed in /opt/RealPlayer/)

if your video card is ati, please change driver from fbdev to radeon

vi /etc/X11/xorg.conf

Section "Device"
Identifier "Card0"
#Option "ShadowFB" "true"
#Driver "fbdev"
Driver "radeon"
BusID "PCI:0:16:0"
Option "UseFBDev"
Option "AGPMode" "4"
EndSection

---

### Post by danns on 2005-07-28
I too have compiled mplayer myself on the PPC side.  Some of the codec support is just not there.  It's been a while since I used it but I do recall that quicktime played without audio and I do not think windows media files played.  But you can get it running!

---

