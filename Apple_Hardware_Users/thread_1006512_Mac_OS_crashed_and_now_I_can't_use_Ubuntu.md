---
title: "Mac OS crashed and now I can't use Ubuntu"
date: 2008-12-09
forum: Apple Hardware Users
---

### Post by kbgabt on 2008-12-09
Hey, I have this huge problem. I have a Macbook 1,1 with dual boot using rEFIt and 2 days ago I upgraded from Hardy to Intrepid, and everything was working well enough (besides the suspend bug). And today, just because I needed iTunes to put music on a friend's iPod, I went to Mac OS X 10.5 and there were some updates waiting (Airport Extreme, iTunes, etc). All of a sudden, after the updates, every single application in Mac OS was crashing (even TextEdit). I turned it off, restarted it and now it goes directly to Mac, which is right now half-dead, because nothing is working, not even Finder or the menu bars, and when I try turning it off the right way, it just stays there and nothing happens.

My question: Is there a way to go to rEFIt before it jumps directly to Mac OS? (it goes directly to Mac OS because the last time I had to turn it off by pressing to off button until it dies.)

If there is such a way? Could you help me with it? And also, if possible, could you tell me how to make Ubuntu the first option for rEFIt?

Thanks.

---

### Post by cyberdork33 on 2008-12-11
> **kbgabt said:**
> Hey, I have this huge problem. I have a Macbook 1,1 with dual boot using rEFIt and 2 days ago I upgraded from Hardy to Intrepid, and everything was working well enough (besides the suspend bug). And today, just because I needed iTunes to put music on a friend's iPod, I went to Mac OS X 10.5 and there were some updates waiting (Airport Extreme, iTunes, etc). All of a sudden, after the updates, every single application in Mac OS was crashing (even TextEdit). I turned it off, restarted it and now it goes directly to Mac, which is right now half-dead, because nothing is working, not even Finder or the menu bars, and when I try turning it off the right way, it just stays there and nothing happens.

My question: Is there a way to go to rEFIt before it jumps directly to Mac OS? (it goes directly to Mac OS because the last time I had to turn it off by pressing to off button until it dies.)

If there is such a way? Could you help me with it? And also, if possible, could you tell me how to make Ubuntu the first option for rEFIt?

Thanks.
That is normal behavior when you have to hard power down OSX. The OSX OS automatically becomes the "blessed" OS. You should be able to hold option on startup and select your start disk from there. You will very likely need to reinstall OSX and restore from a backup as it sounds as though the update was corrupted. 

To make rEFIt boot Ubuntu by default, you have to edit it's config file in the efi folder of your osx partition. The option you want to enable is "legacyfirst"

---

