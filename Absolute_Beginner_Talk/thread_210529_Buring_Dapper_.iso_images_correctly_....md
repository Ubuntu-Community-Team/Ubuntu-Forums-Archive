---
title: "Buring Dapper .iso images correctly ..."
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Thruxomatic on 2006-07-07
Hello all,


When I download the PPC version of the iso, the file ends up 701MB.  No matter what brand of CD-R I try, the largest actual capacity I can find is around 660MB, no matter what the labeling says on the box.  The Disk Utility in OS X won't burn the .iso to the discs as it says the image is too large.  I don't have a DVD burner in my Powerbook, so I'm restricted to using CD-R.  Is there any way to network boot to the image or is there some trick to burning this .iso that is eluding me?

Thanks!

Matt

---

### Post by Dr. Nick on 2006-07-07
I dont have a mac but have you tried this way
[http://www.psychocats.net/ubuntu/maciso.html](http://www.psychocats.net/ubuntu/maciso.html)

You must burn it as a image, you cant just copy the iso to a cd like a data file.

Does the packaging on your cd's say 700mb or 80mins? I dont think you can use the ones that say 650mb / 74mins

---

### Post by Thruxomatic on 2006-07-07
Thanks, Dr. Nick.


It turned out that it was the tool I was using.  Disk Utility in Mac consistently read my 700MB discs as only 660MB, no matter the brand I used or the settings of the utility.  As a result, the .iso was alwasy "too big" to put on the disc.

I found and downloaded the free version of discblaze, a burning utility for Mac and, lo and behold, the same discs now how 702MB each.  I don't know why the native utility for Mac holds back 7-8% of the disc's capacity, but it does.  Burned the .iso this morning and am partway through install on my Powerbook as we speak (posting from g/f's eMac).

---

### Post by Frank Golden on 2006-07-07
> **Thruxomatic said:**
> 
I found and downloaded the free version of discblaze, a burning utility for Mac and, lo and behold, the same discs now how 702MB each.  I don't know why the native utility for Mac holds back 7-8% of the disc's capacity, but it does. 
Mac format overhead maybe. Probably similar to format setup the InCD tool option in Nero places on RW media (you lose some capacity, about 50MB thereabouts). One of the reasons I don't even install InCD with my Nero Suite. Good luck hope it works on your Mac.

---

