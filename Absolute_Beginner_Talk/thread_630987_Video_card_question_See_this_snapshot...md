---
title: "Video card question: See this snapshot.."
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by mdpalow on 2007-12-03
Hey Everyone,

Today I upgraded my entire computer to:

AMD X2 4000
2 gigs of ram
SATA 3.0gig drives
nVidia GeForce 8600 GT 256 megs PCI-E

I first just used the restricted drivers and if you look at my screenshot below, this is what happens when I drag the middle separator down. It's like the video card isn't doing any better than when I had my nVidia GeForce 5200 FX; it did the same thing.

Also, when I drag nautilus around on the screen, it's not quite smooth, but a little choppy.

I went to the nVidia site and downloaded the latest drivers just in case and installed them and it's not doing anything different.

I'm not even running any visual effects.

I haven't added any visual candy; just running straight install.

What's the deal with that? I would have thought the upgraded video card would have no problem and function better.

Thanks...

---

### Post by jordanmthomas on 2007-12-03
You could try using the official nvidia drivers.  (Apparently, you just have to use a restricted driver manager.  I've been out of the Ubuntu game for quite some time, so I can't tell you how to use it.)

Also, you may be surprised to find that things like moving windows and resizing windows are done better when running compiz.  Each window is drawn to a buffer before being drawn on screen and thus you don't get the half-drawn windows you're mentioning.  Even if you don't use any of the fancy effects, it's worth enabling compiz.  (Your card can handle it)

**edit** reread your post, and you're already using the official drivers.  Disregard my first paragraph.

---

### Post by mdpalow on 2007-12-03
so now I'm curious... does everyone have this problem even with a better video card? If so, then I can live with it; otherwise I want to fix it. 

I'll try your suggestion about compiz now and see how it does...

Thanks for the quick reply.

---

### Post by jordanmthomas on 2007-12-03
> **mdpalow said:**
> so now I'm curious... does everyone have this problem even with a better video card? If so, then I can live with it; otherwise I want to fix it. 

I don't know here.  Someone else will need to answer.  I have an integrated Intel chip and my windows draw themselves pretty well even without a composite manager.  Of course, I tend to use light window managers (using awesome at the moment, but I like openbox, dwm, and even enlightenment)

Odds are, you can get better performance without compiz even, but it's at least a temporary fix.

---

### Post by Amstell on 2007-12-04
I would suggest getting rid of compiz.  I had it up and running for a little bit and liked it but caused me a lot of video problems.  Once I reformatted and installed the nvidia drivers everything is working perfectly.  Good luck

---

