---
title: "Mac mini solutions"
date: 2005-03-25
forum: Apple PPC Users
---

### Post by agravain on 2005-03-25
I put together a webpage with my kernel .config and xorg.conf for Mac mini plus a kernel with working sound.

Note that sound doesn't work with the official (stable and unstable) kernels as of yet. A kernel for mac mini with working sound (and the patch) can be downloaded from my webpage (as a debian package, easy to install).

With this kernel I have everything working perfectly (or so I think) except wireless and bluetooth. I don't know how to test the bluetooth support, maybe it works for all I know.

The webpage: [http://www.pvv.org/~perchrh/macmini/](http://www.pvv.org/~perchrh/macmini/)

---

### Post by DJ_Max on 2005-03-25
Good idea, since many people have asked about this.

BTW, wish I had a Mac Mini. :(

---

### Post by billycub on 2005-03-25
How many frames per second are you getting on your Mac Mini?

I have the 1.4Ghz version w/512Mb RAM, running in 1280x1024x24.  I'm only getting 500-600 FPS when I run glxgears.

I figured with a Radeon 7500 I would do better than that... any ideas?

---

### Post by agravain on 2005-03-25
I get about 980 fps. 
I have the options
        Option          "AGPFastWrite" "true"
        Option  "EnablePageFlip" "true"
set in my xorg.conf file. 

Ati doesn't support PPC for their drivers completely, they don't have any openGL-libraries for PPC. With Ati's openGL-libraries installed I suspect we would get a large increase in number of FPS.

---

