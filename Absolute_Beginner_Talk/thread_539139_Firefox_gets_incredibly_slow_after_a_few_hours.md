---
title: "Firefox gets incredibly slow after a few hours"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-08-30
Does anybody else have this problem?  If I have Firefox up for a couple of hours, and even if only a few windows are open, it gets incredibly slow.  I don't experience this with Firefox running under Windows XP.
I'm using the latest Firefox with Xubuntu 7.04.
Am I alone in this, or is anybody else experiencing the same problem?

---

### Post by EtniesBMX on 2007-08-30
check this out, it may help:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")

---

### Post by 5-HT on 2007-08-30
One thing to check is to see if you're swapping a lot when that happens, you can changes the prefs in about:config.
cheers,

---

### Post by Blofeld on 2007-08-31
> **5-HT said:**
> One thing to check is to see if you're swapping a lot when that happens, you can changes the prefs in about:config.
cheers,

Thanks.
1. How do I find out if I'm swapping too much?
2. Which prefs do I have to change in about:config?
    I have entered about:config as URL in Firefox, but am at a loss as to which of the many settings I should twiddle with. :confused:

---

### Post by Hospadar on 2007-08-31
It might also be that over time firefox is either a) leaking memory b) caching too much stuff

Certainly I would think that restarting firefox will solve your problems at least for that session.  In edit->preferences you can set firefox to open up with all the same tabs that were open when you last closed it if you have to restart it.

Also, have a look in your system monitor when firefox starts slowing down, I would imagine that firefox is sucking down way more memory than when you first started it.  If you memory usage is through the roof, this would indicate that your machine is using a lot of swap (if your memory usage is 100%).  you can get to that through System->administration->System Monitor.  You could also do a "top" or "htop" command in a terminal to get the same memory and cpu info.

Try googling around for how to fix firefox memory leaks.  Some of them are just bugs but some are avoidable.  It also might be an addon you are using that is leaking, try disabling addons and see if you get better performance.


Also if you arn't familiar with my nerd-speak  memory leaks happen when programs don't de-allocate their memory, so they arn't using it anymore, but it isn't freed up by the OS for other programs because the OS still thinks that program is using it.

---

### Post by kerry_s on 2007-08-31
> **Blofeld said:**
> Thanks.
1. How do I find out if I'm swapping too much?
2. Which prefs do I have to change in about:config?
    I have entered about:config as URL in Firefox, but am at a loss as to which of the many settings I should twiddle with. :confused:


you don't have to go into about: config for that.
edit> preferences> advanced> network
then just set the cache to the size you want. for example if you want it to use less disk cache set it to 0 for off, 5mb so it repaces old cache with new cache sooner, higher if you want to keep cache longer for faster loading, ya right, cache is tricky, if your stuff is fast, keep a large cache, if it's a bit slow, lower it, you'll get less seek time on the hd, etc...just try a few different settings, all you have to do is clear the cache, if the performance go's back up, it's your cache.

---

### Post by 5-HT on 2007-08-31
> **Blofeld said:**
> Thanks.
1. How do I find out if I'm swapping too much?
2. Which prefs do I have to change in about:config?
    I have entered about:config as URL in Firefox, but am at a loss as to which of the many settings I should twiddle with. :confused:

A few people have answered how to lower disk cache. As to checking your swap usage, you can do it from the system monitor or by entering 'free' into a terminal. Firefox has been known to have some memory leaks, and I've disabled disk cache with some good results.
cheers,

---

### Post by Blofeld on 2007-09-09
Thanks to everyone for guiding me through this curious and wonderful jungle that is the electronic computing machine.  I have learned a lot from this thread.
I have fiddled with the Firefox disk cache, but so far the only obvious consequence was that YouTube videos hung every few seconds with disk cache set to zero.
For now I will have to abide with restarting Firefox every now and then.

---

### Post by st33med on 2007-09-09
Ah, that is bug. It will get fixed, but it has been awhile since I have heard anything from Adobe about flash.

---

