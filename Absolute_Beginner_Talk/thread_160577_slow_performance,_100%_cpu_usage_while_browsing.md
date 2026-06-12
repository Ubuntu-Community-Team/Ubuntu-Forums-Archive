---
title: "slow performance, 100% cpu usage while browsing"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by kwyjibo on 2006-04-15
Back already!  I'm really sorry if this has been asked a million times before, I have done a search and not seen any obvious answers though.

Not sure if it's related to browsing, but have found that in the past hour or so while browsing I have had a few issues.  one was a complete system freeze, mouse moved but no response and had to reset.  More common though is as i'm browsing between pages it eventually starts slowing down, the cpu usage goes to 100% and the pages aint 'drawn' properly (have to move mouse over the page for it to show bits) and i then gotta prett ctrl-alt-backspace to sort it.

Now i did recently do an update to firefox 1.5.0.2 via a script i found in the HOWTOs, so was wondering if that could be it.  But is there easier ways to diagnose, see whats happening?  or is this a known issue.

any help would be greatly appreciated, and i apologise for all my questions!

---

### Post by bscbrit on 2006-04-15
Unfortunately, this is not uncommon with Firefox - this is the second thread today!  It does seem (to me, at least) to be related to the maximum number of tabs that I have opened simultaneously.  If you frequently have more than 5 - 10 tabs open (as I do) then you might try limiting them to a more manageable number.  This is not a fix - it has simply helped dissuade me from uninstalling what would otherwise be a superb browser.

Try reading this thread: [http://www.ubuntuforums.org/showthread.php?p=923983#post923983](http://www.ubuntuforums.org/showthread.php?p=923983#post923983)

---

### Post by kwyjibo on 2006-04-16
i've been playing around a bit and last night i installed the proper nvidia drivers for my graphics card (6600) then reconfigured X... it's definitely made a difference to video playback, screensavers and all that jazz, and whether or not it's coincidental, i've been keeping an eye on cpu usage when firefox loads pages and it seems to take a lot less processing now.  Haven't really had a ton of tabs going since, but will see how it goes.  I'm sure to shout if it hasn't worked  ;)

---

### Post by bscbrit on 2006-04-16
This will be interesting if it develops - most people seem to think that the problem is memory leakage but if, in some way, it is connected with a specific driver.....

I'll stay subscribed to this thread for a while...

---

### Post by jhaykage on 2006-04-16
Now I remember, I use a lot of tabs in Firefox. Like there would be some 4 main windows but then each would probably have at least 5 tabs open.

Hmm..I'll try to cut down on the tabs usage and I'll also look into making sure my current NVidia card driver is well suited for Ubuntu.

Thanks guys!

---

### Post by kwyjibo on 2006-04-16
probably gonna jinx myself here but it's been going alright so far.  I've been doing a bit of monitoring while browsing and every site i've been going to I've opened in a new tab.  In the end I had 2 FF browsers running both with around 10 tabs in them, was flicking between the tabs, scrolling, clicking, downloading and all stayed stable.  CPU usage was up a bit understandably, but if i sat idle it would fluctuate and peak at around 40% (whereas before once the slowdown happened it wouldn't leave 100%).

Now as i said, could be coincidence - but all I did was update nvidia graphic card drivers, and reconfigure X (to look at new card drivers, everything else was pretty much default).  Oh i also changed back the owner of firefox directory to root, although i don't think that would cause any performance issues.

---

