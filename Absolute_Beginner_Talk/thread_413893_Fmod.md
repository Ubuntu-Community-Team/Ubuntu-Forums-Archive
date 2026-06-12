---
title: "Fmod"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-04-19
Has anyone ever installed Fmod?

I install a game called "Racer" from [Racer]("http://www.racer.nl/")

But had an error something to do with Fmod, but when I downloaded, which I think was the correct version and untar it there was no readme or install file to tell you how to install it!! :confused: 

So has anyone managed to install Fmod??

Thanks
Ian

---

### Post by natirips on 2008-02-21
I have the same problem, when I try to start the game it says
```
natirips@natirips-laptop:/usr/local/games/racer$ ./racer
--- application start ---
** [racer/7026] Can't open log file (QLOG)
QApp: new QDisplay
Racer version: 0.5.3 beta 6 (Mar 19 2007/21:40:23)
** [racer/7026] Can't open log file (QLOG)
RMultiview:Create()
Multiview: we are the master/server
### Q Memory Report - no allocations ###
### Q Memory Report - no allocations ###
QImage::Read("data/fonts/din14.tga")
QLicensePool (RMGR:Create):
QImage::Read("data/images/skidmark.tga")
QImage::Read("data/images/smap_whitesun_add.tga")
QImage::Read("data/images/track_lt.tga")
QImage::Read("data/images/track_rt.tga")
QImage::Read("data/images/track_up.tga")
QImage::Read("data/images/track_dn.tga")
QImage::Read("data/images/track_fw.tga")
QImage::Read("data/images/track_bw.tga")
QImage::Read("data/images/sun_lt.tga")
QImage::Read("data/images/sun_rt.tga")
QImage::Read("data/images/sun_up.tga")
QImage::Read("data/images/sun_dn.tga")
QImage::Read("data/images/sun_fw.tga")
QImage::Read("data/images/sun_bw.tga")
RAutoJoin:Create()
Autojoin: we are the master/server
QImage::Read("data/images/repbuts.tga")
Can't init FMOD
** [racer/7026] Can't open log file (QLOG)

```The disturbing part is the line before the last line I think.  I do have FMOD installed (I got it from [www.fmod.org](www.fmod.org) ).

Edit: I've noticed that some sort of window with scrambled pixels opens for a fraction of a second, but then it closes suddenly and the game exits.

---

