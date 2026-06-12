---
title: "Ubuntu bootup Freezing due to wireless?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by OhioYJ on 2007-11-04
Ok I've been running into a weird problem. My desktop freezes every so often when booting Ubuntu, it gets to the screen where the orange bar goes across as its loading but stops. However it doesn't do it all the time, sometimes it will boot fine for a week, then all the sudden it won't boot. Restarting does nothing, I have to power it down and wait a few seconds, then sometimes it will start, sometimes it will still freeze. Windows boots fine, even when Ubuntu doesn't. 

I ran every stress test I have, its not faulty piece of hardware. So I disabled the splash screen, and it stops at this point:

[15.348000] HOSTAP_PCI: Registered NetDevice WiFi0

So it appears that its something to do with my wireless card, which does NOT work in Ubuntu. I've never been able to get it work in Ubuntu, but it works fine in Windows. 

Is there a way to disable this?

Ubuntu 32-bit,  7.04 by the way.

---

### Post by rudeboyskunk on 2007-11-04
Is there a way to disable it in your BIOS?  I doubt it, but worth a shot.  It would be easier than taking it physically out of your computer each time you wanted to boot into Ubuntu.

You could also try to make it work using ndiswrapper.

Is it listed at all under your list of network devices when you go into Network settings?

---

### Post by OhioYJ on 2007-11-04
> You could also try to make it work using ndiswrapper.

Yeah I tried that, I couldn't get it to work right.

> Is it listed at all under your list of network devices when you go into Network settings?

Yes, Ubuntu sees it, just can't use it.

---

### Post by OhioYJ on 2007-11-05
Bump.....

---

### Post by OhioYJ on 2007-11-07
Bump..... 

Still having the problem.....

---

### Post by OhioYJ on 2007-11-08
Is there just a way to disable hardware somewhere in ubuntu?

---

### Post by twiceasworn on 2007-11-08
I believe you should be able to blacklist it in /etc/modprobe.d/blacklist.  I had to do this for my onboard graphics in order to get dual monitor to work.  I have no clue exactly what you would need to put in there to blacklist that specific card.  But that's where I would start looking.

---

