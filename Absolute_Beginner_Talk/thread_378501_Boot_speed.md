---
title: "Boot speed"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Bideshi on 2007-03-07
We really want to like and use Ubuntu but we cannot live with our boot speed.  We have just bought a P4 3Ghz HT, 512 MB RAM, 80 GB HD (50 of which are running Ubuntu 6.06) desktop.  It takes less than one minute to boot up Windows XP on the remainder of our HD but 15 minutes to boot Ubuntu.

We cannot believe it should take this long.  Are there any simple steps that we can take to improve things?  We checked some of the older threads on this issue but saw comments about slow 2 minute boot ups and some complex looking solutions and felt our problem (and hopefully, solution) may be a bit different.

Please help.

---

### Post by shanepardue on 2007-03-07
Wait, on a clean install of ubuntu, you're waiting 15 minutes for it to boot? Is this an exaggeration? There's definitely a problem if it takes that long.

---

### Post by aeiah on 2007-03-07
it'll be taking that long because the system is looking for something or struggling with something for ages. if its taking so long its quite plausable that its some feature you dont even have so you can probably get rid of it.

have a look at your boot log. its at /var/log/boot i believe. you may be able to spot which bits its hanging on or post it up here and people may be able to see a problem.

---

### Post by bks on 2007-03-07
Does this happen even with LiveCD?

---

### Post by gigaferz on 2007-03-07
Just keep trying, hopefully after a few weeks or so It might be faster, sometimes 3 minutes, 8 or maybe 1,

Also reinstalling will not help either. I did it a couple of times. there are some guys that have the same problem but,  nobody know for sure if its software or hardware related.

Usually it is when its "loading restricted driver" when it takes the longest.

I have a very old gateway and it has always been booting in 1:20, but the newer machine is always acting weird.

Good luck at if you find a solution or any help , please let me know.

Thank you.

---

### Post by DarkN00b on 2007-03-07
It definitely should not be taking that long to boot. My machine laptop takes about 33 seconds to boot. Try installing Bootchart from Synaptic or type

```
sudo aptitude install bootchart
```

This will give you a .png picture in /var/log/bootchart that shows how long every boot process runs. That should help you diagnose your problem.

---

### Post by Bideshi on 2007-03-07
Thanks for all the posts.
1. Yes it really does take this long!
2. It was just as slow using the live CD.
3. We will look at the boot log and boot chart and post anything that may help later.  (we're noobs and don't have much of a clue - it was a miracle we got it loaded in the first place)

---

### Post by Bideshi on 2007-03-07
So, 5 mins after posting our last message, we logged on to get the above info and ubuntu loaded virtually straight away.  We rebooted it to check we weren't dreaming and it took less than a minute.  Thanks for your help, your good thoughts obviously worked their magic?!  Why this didn't work yesterday when we rebooted a couple of times, each at 15 mins, I don't know.

---

