---
title: "How to create DVD from AVI in Ubuntu?"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by nir78 on 2006-04-09
Hi,

In win I just used nero and everything done auto.
Does Ub have a similar tool ?

Nir

---

### Post by Mustard on 2006-04-09
I'm not too sure.  You could try something like k3b or another dvd authoring application.  Try a search in Synaptic using the keywords dvd author and read the descriptions of the applications that come up.

---

### Post by taurus on 2006-04-09
You can try DeVeDe, tovid, or some other programs.  It has been posted a few times here so use the Search option for those...  In the meantime, here are the links for those two apps!

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)
[http://tovid.berlios.de//en/index.html](http://tovid.berlios.de//en/index.html)

---

### Post by jtpratt on 2006-04-25
I learned the hard way, converting video in Linux is painful compared to Windows.  There are only a few libraries for doing this (ffmpeg, dvdauthor) and tons of programs that provide a front end to them.  Also (in usual Linux fashion), many of them only do part of the job.

Unlike point and click in one program in Windows, in Linux you have to break down the parts of what you want to do:

1.  Rip the DVD
2.  Encode the DVD
3.  Burn the DVD

Some programs work better.  K3B (mentioned earlier) doesn't yet do encoding.  Tovid or DeVeDe might come closest to what you want - or maybe even AcidRip.
check out my [Ubuntu Video Conversion Guide]("http://smorgasbord.net/convert_video_linux") for the solutions I found.

---

