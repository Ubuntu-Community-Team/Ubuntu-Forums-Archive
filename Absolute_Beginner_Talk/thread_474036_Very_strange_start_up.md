---
title: "Very strange start up"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by readitsideways on 2007-06-14
Ok, I've been fiddling, and got into a fiddle.

I was trying to get a better resolution on my laptop and tried all sorts of things, only to discover that the limiting factor was my screen. 

Then I undid all the fiddles (put the old xorg.conf back, uninstalled 915 resolution). Now when I start up, beryl and my start up apps take forever to load - but its not just beryl, everything that appears in my notifier - wireless login, gaim, beryl, skype etc.

I've tried removing startup programs from the start up session to see if I could see what the delay is, but none of them (not even beryl) made a difference.

It seems that once the wireless login (key chain) pops up then every loads, but it did always load first, so it may just be that once whatever is holding things up is done, then everything loads as normal.

I have noticed that if I start beryl manually while waiting for the start up stuff to load then the splash screen appears again and stays there for some time before it loads.

Any ideas?

Duncan

How do I find what the culprit is?

---

### Post by readitsideways on 2007-06-14
I've tried removing all start up sessions and reduced services to a minimum, but same problem. There is also this splash screen delay if I ctrl>alt>backspace

By splash screen I mean the Ubuntu start up splash screen that says 'Nautilus' under some icons. THe rest of the desktop loads fine, just no window borders (beryl) or wireless - for a while at least (2-3 min)

Pulling my hair out...

---

### Post by readitsideways on 2007-06-15
Found the culprit, but how to fix?

From my logs:

```
Jun 15 08:26:34 duncan-laptop kernel: [  200.184000] apm: BIOS not found.
Jun 15 08:26:34 duncan-laptop kernel: [  200.736000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Jun 15 08:26:34 duncan-laptop kernel: [  200.904000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jun 15 08:26:34 duncan-laptop kernel: [  200.904000] NFSD: starting 90-second grace period
Jun 15 08:29:07 duncan-laptop kernel: [  353.172000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
```

90 second grace period ... yep that's it. That BIOS not found also worries me...

---

### Post by ironmonkeygf on 2007-07-12
Did you ever find a solution?  I'm having the same problem.

---

### Post by Al3xK3aton on 2007-07-12
A clean install should solve this problem. If you don't want to do a clean install, why not try changing the settings back to before so that you can use higher resolution like you originally intended, and just get a new monitor that supports that resolution. You can get a good, large LCD screen for only a few hundred dollars.

---

### Post by ironmonkeygf on 2007-07-12
I didn't mess with my resolution settings when I started getting the NFSD error.  I've got a laptop, so changing resolutions isn't really an option.  What is NFSD and how else could I have messed it up?  Is it only tied to the video display?

---

### Post by p_quarles on 2007-07-12
> You can get a good, large LCD screen for only a few hundred dollars.

Sure, but wouldn't that kind of defeat the purpose of owning a laptop?

---

### Post by ironmonkeygf on 2007-07-12
I finally got mine fixed.  Somehow my wired connection got enabled.  I unchecked the box for my wired connection in System>Administration>Network and the slow login is gone.  Apparently the 90-Second GracePeriod had nothing to do with the slow desktop because I still get that message in kern.log.  Hope this helps someone...

---

### Post by readitsideways on 2007-07-13
Mine just sorted itself out. It may have been the wired network problem above.

---

