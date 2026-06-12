---
title: "pharos gps-500 with Ubuntu?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-11-11
At this point in time I don't care WHICH program I use for GPS, I just want one that works.

I have MS Streets Trips and the GPS device that came with it, which is the Pharos GPS-500 (a search for this device on this forum returned no results.  There are some posts about the gps-360, but no on the 500)

I've searched many threads on this forum about GPSDrive and also using MS S&T in WINe. Most people seem to be using GPSDrive, but I can't get it to work with this Pharos GPS-500.  I changed the settings in the Prefs to reflect what is found in dmesg:

```
[56436.976000] usb 1-1: pl2303 converter now attached to ttyUSB0
[56436.976000] usbcore: registered new interface driver pl2303

```

But GPSDrive just freaks out when I launch it.  It shows some location in Berlin, I think, and it says that I am moving, but I am not.  The dials are move around like I am in a freaking airplane or something.  So it doesn't really act like it is detecting my Pharos.  I also have gpsd installed, per the gpsdrive website, but that doesn't seem to matter either.

As far as MS S&T goes... what I have read on this forum suggests that it doesn't work too well in Wine.  I have also read this post:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3962](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3962)

However, the new Gutsy OS seems to use WINe much better and this WINe doc is kinda out-dated.  So I might go ahead and try this prog in Gutsy and see what happens.

Has anyone gotten ANY GPS program to work in Ubuntu with this setup?

---

