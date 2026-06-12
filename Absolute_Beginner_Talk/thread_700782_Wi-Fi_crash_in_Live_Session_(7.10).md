---
title: "Wi-Fi crash in Live Session (7.10)"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by BumberBot3K on 2008-02-18
So I've got a Ubuntu 7.10 64-bit Live CD that I was using to fiddle around with Ubuntu, to see if it's a suitable replacement for me. I've popped it into my Gateway MX3417 notebook. Start up works OK (in Graphics Safe Mode), but if I try and connect to my home (WPA security) wireless network, the connection animation begins, and a few seconds later the computer completely locks up. Only a hard power down will turn it off. The only other clue is that my Caps Lock LED blinks regularly after the lock. Gateway, of course, has no documentation on what this blinking could mean.

Any thoughts? Thanks in advance.

BB3K

---

### Post by randy78 on 2008-02-18
The only thing that I can suggest is to try reburning the disk at a very slow (3x) speed...

Good Luck

---

### Post by BumberBot3K on 2008-02-18
Thanks for the thoughts. I did run the CD check from the boot menu, and it checked out. Is it still possible for it to be a bad CD?

---

### Post by randy78 on 2008-02-18
Hmm...

It still could be a bad cd, but more importantly, how much RAM is currently installed?

Just to rule it out, go ahead and burn another disc at a very slow speed (if you have the extra discs) and try it out...

---

### Post by BumberBot3K on 2008-02-18
I have 1GB of RAM in this machine. 64MB or so is taken by whatever graphics chip is in this thing. I will re-burn a CD, I've got plenty (thanks CompUSA!)

I tried to run a live session on other PCs in the house, but I've just discovered that I'm the only one with a 64-bit processor!

Thanks .. I will report back after I've tried another disc.

---

### Post by randy78 on 2008-02-18
Sounds good.

Bulk CD's and DVD's rule!

---

### Post by BumberBot3K on 2008-02-18
Well, while I waited for my new CD to burn on another machine, I figured I would try to eliminate another issue. I booted the live session and attempted to connect to a neighbor's unprotected wireless connection, and it's working! I am about to attempt a disconnect from this network, and a re-connect to my own encrypted network. If it freezes that perhaps its a wireless adapter driver problem? I'll be back...

---

### Post by randy78 on 2008-02-18
Hmm...

You could also disable Roaming Mode in Network Manager and set a Static (or DHCP) IP by hand and see if that will help...

---

### Post by BumberBot3K on 2008-02-18
Same results with the replacement disc. I will try manually entering the information next.

EDIT: I turned off Roaming and entered info manually. While the system didn't freeze, it wouldn't connect either. The "antennae" icon in the upper left switched to the "dual computer" icon, and said "Manual Configuration" on hover. The machine took the settings, but loading FireFox gave me no connection. I couldn't even connect to my router's IP address. I don't know enough about Ubuntu networking tools to get any more info - was I supposed to take an additional step after manually entering all the network info?

I'm sure this problem is compounded by running a live session instead of attempting a clean install, but unfortunately my Gateway doesn't have proper Windows recovery CDs and relies on a HD partition to restore... I don't want to blast away my current install until I'm satisfied I can recover the factory settings! It actually came loaded with a non-iTunes attached QT player, and that's worth its weight in gold!

Thanks again!

---

### Post by randy78 on 2008-02-18
I just detailed how to set up a static IP address in another post:
[http://ubuntuforums.org/showthread.php?t=700360]("http://ubuntuforums.org/showthread.php?t=700360")

Take a look at it and try what I outlined to see if that helps.

Take Care
Randy:popcorn:

---

### Post by BumberBot3K on 2008-02-18
Thanks for your help Randy. I tried the static IP address, both inside and outside of the router's DHCP assignment range. No luck. I have now plugged my machine directly into the router, and there are no issues there.

At this point, I think the problem is such that I would prefer to do a clean install and tackle it there, rather than haggle with a Live Session. There are other issues too, like the display resolution and no audio, that aren't worth dealing with without a real install. Of course, this means figuring out how to back up my current XP install... Gateway of course wants $$$ for full recovery CDs, and I don't have burning capability, so it'll be tricky!

Once I figure it out and have a clean Ubuntu install to wrestle with, I will be back to harass you!

Thanks again for your thoughts!
BB3K

---

### Post by randy78 on 2008-02-18
Sounds good ;)

Gimme a shout if you need any help 

Randy

---

