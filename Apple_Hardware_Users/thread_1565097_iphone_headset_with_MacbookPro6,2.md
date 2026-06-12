---
title: "iphone headset with MacbookPro6,2"
date: 2010-08-31
forum: Apple Hardware Users
---

### Post by smgoller on 2010-08-31
I've been trying to get my iphone headset microphone working with my macbook pro with no success. Does anyone know how to get it running? The headphones part works fine.

---

### Post by dngfng on 2010-09-01
Just to confirm: you are talking about the regular iPhone headset (not bluetooth) that comes along with every iPhone.

If that is the case have you checked if your microphone is working in Ubuntu at all?

It could be that the input channel is muted - have a look in alsamixer to check that the channel is open.

---

### Post by smgoller on 2010-09-01
Yes, not bluetooth. alsamixer doesn't seem to show a microphone port at all, just a "capture" port, which I presume is the other physical audio jack. Under MacOS, I can plug in the wired iphone headset, and get audio and microphone support from a single port. This doesn't seem to work under linux.

---

### Post by dngfng on 2010-09-02
oh - just figured it out.

The iPhone is a single plug for both audio in- and out-put. 
However our MBP's (and all Notebooks known to me) have separate ports for audio in and audio out - so off course it will not work using the iPhone's Headset. At least you can use them as a headset...

---

