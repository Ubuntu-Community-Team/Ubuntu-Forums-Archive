---
title: "Linux versus Windows use of swap file"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Jake808 on 2007-04-21
I haven't been using Linux for long but I have found that Linux seems to access the hard drive less when it is running than WinXp did.  When you run a program in windows its seems to use the hard drive more. When on windows my hard drive light always flashed regularly and my hard drive would often burst into life for no reason.   Do the two operating systems use swap space differently?

---

### Post by codingmaster on 2007-04-21
Hello!

Both system kernels use different swapping techniques and different achievements.

I hope this will provide some interesting information for you:
[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

Best regards, Georgy Berdyshev

---

### Post by freebird54 on 2007-04-21
LInux uses your memory to cache recently accessed disk files - and thus hits the drive less often in normal use.  If more memory is needed it flushes the cache, and uses the freed memory.  Only then would it hit the swap fle, if completely out of memory.  With 1Gb of RAM or more , you may never hit the swap in Ubuntu!  (I rarely do with 512).

Hope this helps!

---

### Post by Jake808 on 2007-04-21
Yeh that is a good explanation. :-)  What does windows do?  What does it do differently?

---

### Post by milton1 on 2007-04-21
Windows can use ram to cache files, but it is not a default setup. Also, windows is often slower to respond with writing and reading the swap file (pagefile in ms terminology), because the file is not set to a fixed size by default, and it is placed on the same partition as the rest of the os. This leads to the virtual memory file becoming fragmented and slow. I imagine you could create a dedicated ntfs partition and set windows to use the entire partition as pagefile; this would at least eliminate the fragmentation problem. If it were on a different physical drive, it could even be faster.

---

### Post by freebird54 on 2007-04-21
I am not a Windows dev, but AFAIK it will not cache the drive even if it has memory, and some of its programs will internally swap parts in and out in an effort to 'save' RAM.  I am suspicious that other thaings are hittiing the drives too in the background - but that may just be prejudice talking (and paranoia!).  However, I use a RAM monitor on Win, and it rarely drops below 100 Mb free, and yet the drive gets hit a lot...

---

### Post by Zeroangel on 2007-04-21
> **milton1 said:**
> Windows can use ram to cache files, but it is not a default setup. Also, windows is often slower to respond with writing and reading the swap file (pagefile in ms terminology), because the file is not set to a fixed size by default, and it is placed on the same partition as the rest of the os. This leads to the virtual memory file becoming fragmented and slow. I imagine you could create a dedicated ntfs partition and set windows to use the entire partition as pagefile; this would at least eliminate the fragmentation problem. If it were on a different physical drive, it could even be faster.
I should add since it was implied (not explicitly stated) that you can configure windows to use the swapfile more efficiently, if you open the system [win+pause/break] panel, go to the advanced tab -> performance -> virtual memory -- and set the swap file to a fixed size (512MB or so is usually sufficient)

It works rather well on Windows machines.

---

### Post by milton1 on 2007-04-21
> **Zeroangel said:**
> I should add since it was implied (not explicitly stated) that you can configure windows to use the swapfile more efficiently, if you set it to a fixed size using the system [ctrl+pause/break] panel, going to the advanced tab and finding the options which allow you to adjust those parameters.

It works rather well on Windows machines.

True. I have done this myself, many times. I often wonder why it is not a default setting. However, by the time I had the idea to create a dedicated swap partition in windows, I had already dumped ms completely in favour of kubuntu.

---

### Post by freebird54 on 2007-04-21
Trying to simplify setup I guess.  Also - it defaults to the end of the partition, slowing it down.  If you were to force a fixed size on an 'early' partition of its own, it would be considerably faster.

---

### Post by Jake808 on 2007-04-21
Yes I know the paranoia bit....you end up thinking "why is windows churning away writing and reading to your hard drive when you are maybe just writing an email...or just leaving your computer idle for a few minutes... Even the cleanest and most slimmed down install of Xp seems sluggish compared to what I am experiencing on Ubuntu.  But I really shouldnt be comparing with Xp  after only being in the Linux world for 2 days :-P A world I must say is seems to be free from clutter and that feeling of being knee deep in syrup I have had with Windows.

---

### Post by milton1 on 2007-04-21
> **freebird54 said:**
> Trying to simplify setup I guess. 

I could see that, but so many systems run at least two partitions by default anyway (one for restore functions), why not add one more small one?

---

### Post by freebird54 on 2007-04-21
Probably an elitist thing.  If you know enough to want it, you will probably blow away the original install and crapware, and setup your won way anyhow!  Perhaps some oem does this for its business customers?  Would certainly be a selling point if they let it be known (along with other optimizations)  

Let's not get TOO far off-topic here - still in Absolute Beginners Forum after all! :)

---

### Post by milton1 on 2007-04-21
> **freebird54 said:**
> Probably an elitist thing.  If you know enough to want it, you will probably blow away the original install and crapware, and setup your won way anyhow!  Perhaps some oem does this for its business customers?  Would certainly be a selling point if they let it be known (along with other optimizations)  

Let's not get TOO far off-topic here - still in Absolute Beginners Forum after all! :)

Fair enough, but perhaps we can inspire some absolute beginners to try tweaking their systems and making them that much better. :)

---

### Post by freebird54 on 2007-04-21
I guess if we talked about Ubuntu tweaks!  Hmmm - kill off Bluetooth if you don't use it, and the CPU scaling if it doesn't apply?

EDIT:  System->Administration->Services  :)

---

