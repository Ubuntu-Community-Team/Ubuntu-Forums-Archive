---
title: "Is windows making the race after all?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by seng1978 on 2007-08-10
As a windows user I have to say using ubuntu I have spend so far way more time on ubtuntu forums then in windows forums.  I cant find a single article talking about how to get IP or Network Cameras running on Firefox. I have a home surveillance with a couple VIVOTEK cameras.
The cameras webserver is written for IE only I guess. It is very convenient using IE as it automatically asks to install the MPEG4 plug-in. 
So any solutions? Or should I give up linux then..

By the way, Vivotek has DVR software(windows of course) any suggestions so I can use something similar to that as well?

Seng-der orkenfuehrer

---

### Post by SOULRiDER on 2007-08-10
I solved the problem of enbedded video in firefox by installing mplayer and mozilla-mplayer.
Any aditional codecs you install should still work on firefox so no problem there. Bottom line, you can still use windows with VMWare, although it may be a bit uncomfortable.

To install mplayer and the plugin for firefox type:

```
sudo aptitude install mplayer mozilla-mplayer
```

(Just installing mozilla-mplayer should install mplayer since its a dep, but just add it anyways :P)

---

