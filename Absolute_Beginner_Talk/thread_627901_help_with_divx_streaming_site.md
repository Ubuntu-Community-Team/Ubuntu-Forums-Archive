---
title: "help with divx streaming site"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by NeoEIRE on 2007-11-30
hi
i want to watch this tv-series, the site uses Divx, and when i 1st go to the site theres a note on the video window saying "linux users try Mplayer"

[URL="http://www.stage6.com/user/dodge1986/video/1613777/stargate-atlantis-season-3-episode-1"]
http://www.stage6.com/user/dodge1986/video/1613777/stargate-atlantis-season-3-episode-1[/URL]

but i dont know how i would do that... can someone have a look for me... 
if i'm not making sense then us the link and u'll see.

thanks
neoeire

---

### Post by fineas on 2007-11-30
[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by NeoEIRE on 2007-12-03
hi
sorry it took so long to reply, i have them files installed and mplayer... 
i would usually just right click, open with... then choose which program, but i cant find anything to right click to get them options... and the divx window with us linux mplayer just goes to the install program with usually came up with flash content.

i have to admit, as much as i dislike windows, ubuntu problems beginning to get annoying...

---

### Post by FuturePilot on 2007-12-03
Did you install the Firefox plugin as well?
```
sudo apt-get install mozilla-mplayer
```
Restart Firefox then. 
Also make sure you have all the codecs installed
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by NeoEIRE on 2007-12-03
i have done then, and tried... nothing happens, it just asks to install manually with dix player...

which still doesnt work, i am using 7.04... is all the bugs out of 7.10?????

---

### Post by FuturePilot on 2007-12-03
> **NeoEIRE said:**
> i have done then, and tried... nothing happens, it just asks to install manually with dix player...

which still doesnt work, i am using 7.04... is all the bugs out of 7.10?????

Ah, 7.04. I think there was a small bug with linking the divx mplayer plugin. Can you post the output of
```
ls /usr/lib/firefox/plugins/
```

---

### Post by NeoEIRE on 2007-12-03
neoeire@neoeire-desktop:~$ ls /usr/lib/firefox/plugins/
flashplayer.xpt        mplayerplug-in-rm.so    mplayerplug-in.xpt
libflashplayer.so      mplayerplug-in-rm.xpt   npwrapper.libflashplayer.so
libunixprintplugin.so  mplayerplug-in.so       oldtotemfiles
mplayerplug-in-qt.so   mplayerplug-in-wmp.so
mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt
neoeire@neoeire-desktop:~$

---

### Post by FuturePilot on 2007-12-03
Yep, try this
```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/
```
This will link the mplayer divx plugins correctly to the Firefox plugins directory.
Restart Firefox.

---

### Post by NeoEIRE on 2007-12-03
nice1 mate, ur a life saver.... 

:guitar::lolflag::popcorn::popcorn::lolflag::guitar:

---

### Post by FuturePilot on 2007-12-03
You're welcome! :guitar:

---

### Post by stolid_agnostic on 2007-12-15
> **FuturePilot said:**
> Yep, try this
```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/
```
This will link the mplayer divx plugins correctly to the Firefox plugins directory.
Restart Firefox.


wow you're a genius mate!   I had tried everything and just those two commands fixed it all! cheers!

---

