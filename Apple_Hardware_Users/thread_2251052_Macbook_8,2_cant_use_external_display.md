---
title: "Macbook 8,2 cant use external display"
date: 2014-11-01
forum: Apple Hardware Users
---

### Post by indifference on 2014-11-01
Hello,

Since I bought my macbook pro in 2011 i've tried every ubuntu release to see if I could use it as my default develop OS.
Well, every stock release failed so far and as I didn't have time to mess around with it I always ended giving up.
So here we are again with version 14.10 to see if we can get this working ;)

This macbook has a dual GPU: a AMD Radeon HD 6750M and a Intel HD Graphics 3000.
I don't care about GPU switching, I just need one and my external monitor connected via display port working.

Since Intel is well supported in Linux, I searched the internet and found some grub commands to disable the discrete GPU and use the integrated instead:

```
outb 0x728 1
outb 0x710 2
outb 0x740 2
outb 0x750 0
```

Ubuntu boots fine and everything seems to work.. except the external monitor.
In the screen configuration panel I can see that the external monitor IS detected but nothing is displayed.
In the logs theres several of messages like this:

```
too many voltage retries, give up
failed to train DP, aborting
```

Can someone help me? ):P

PS: I've tried installing the AMD proprietary drivers and ubuntu can't even boot up with those.

Thanks and kind regards,

Pedro Saraiva

---

### Post by slickymaster on 2014-11-01
*Moved to the ***Apple Hardware Users*** sub-forum*

---

### Post by este.el.paz on 2014-11-03
@PS:

I don't have any experience with the external monitor in linux . . . although I'm thinking about running a screen from my iBook in the near future.  Couple points . . . I have seen where "AMD" might cause problems for linux.  However, in testing the recent beta of 14.10 there have been some "radeon" issues . . . which again, not sure if this is correct . . . but, might try "video=ofonly" on boot, or something with "radeonfb"???? and the screen resolution numbers.  I had to enter such boot params to get 14.10 to work . . . in PPC.

But, perhaps try 14.04 . . . LTS, I had 14.04 Xubun running on my '10 MBPro . . . and now it's LM17 . . . which is built on top of 14.04 . . . .  And, when you do the install is your external monitor plugged in?  How about using the LiveDVD . . . did you test the system **with the external monitor set up as the screen you want***?

And, then, after install running "additional drivers" . . . anything show up?  Also, md5sum number checks out OK on the iso??

e.e.p.

---

### Post by petersphilo on 2015-02-05
My understanding is that, even in MacOS, you cannot run an external monitor on the Intel chip alone:
You must have 'graphics switching' or the Readeon enabled to run the external display..

See [this documentation of gfxCardStatus]("https://gfx.io/howto.html#displays") as an example (section 3 on external displays)...

i hope this helps..

---

