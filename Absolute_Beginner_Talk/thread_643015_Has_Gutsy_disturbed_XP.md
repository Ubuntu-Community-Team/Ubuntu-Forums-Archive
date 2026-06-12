---
title: "Has Gutsy disturbed XP"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2007-12-17
Since making my xp machine dual boot with Gutsy, XP cannot seem to remember its configuration settings. I have to re-install my scanner every time I use it, the ext2 extension sometimes fails to read the ext3 drive, etc. On the other hand, Ubuntu frequently will not boot after a Windows session at all, putting up an "Unexpected Response" error mesage which repeats indefinitely. 

I can't image how this could be true, but it _seems_ that if a significant amount of time passes between moving from one machine to another, everything works ok, mostly.

I checked out all the drives, and the are clean. The hardware has not changed. Can anyone suggest any other factor which might bother both machines? Is it possible that some piece of hardware retains a bad bit of data more than a few seconds after shutdown? 

Too wierd for me ...

Gary

---

### Post by amoghvc on 2007-12-17
Something similar used to happen to me on openSUSE 10.2. When I used openSUSE and then rebooted the machine and got into Windows XP, it would not detect my LAN card and report that the network connection was unavailable. If I powered off the machine instead of a plain reboot, then booted into Windows XP directly, the LAN card would work.

The answer to the problem is that Linux (openSUSE 10.2) and Windows XP left the LAN card in different states when they were done using the device, openSUSE actually turned off the device and this confused Windows XP when I did a reboot. But a Turn Off and Boot to Windows XP never gave me problems.

So, yeah, the gist is that Linux and Windows leave devices in different states and that might be what is causing this kind of behaviour. Instead of a restart / reboot if you did a Turn Off and then booted into the OS that you want, it may solve your problem.

Also, you can always go into detail, if the options are available, and control how Linux deals with your device and customize it. But I advice against it, cause it might damage hardware. Though I might be wrong and some Ubuntu gurus may be able to help you there.

Hope this helps.

cheers,
Amogh

---

### Post by Gary Nored on 2007-12-17
Aha! So they _can_ leave lasting changes! One thing I noticed a day or so later is that if the machine had been off for awhile (10-15 minutes) things seem to work ok. Too bad I didn't know that when I was under deadline pressure from a publisher :~

I'll look into the exit settings of these two creatures and see if I can locate the incompatibility. 

Thanks for your reply.

Gary

---

### Post by tgalati4 on 2007-12-17
Many ethernet chipsets contain data (ip addresses, mac addresses, and performance information) that is retained until the machine is completely powered down.  This normally improves performance of the card, but can trip up a dual boot situation.  It's normal and something to pay attention to when dual booting.  Some graphics cards behave the same way.

---

