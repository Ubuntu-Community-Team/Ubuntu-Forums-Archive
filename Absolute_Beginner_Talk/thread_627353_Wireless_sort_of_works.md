---
title: "Wireless sort of works?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by OhioYJ on 2007-11-30
Ok so I installed Ubuntu to my wifes laptop (ze4430us HP laptop), which has the Broadcom 4306 chipset for wireless. I've just used bcm43xx-fwcutter for all my other laptops, and I've tried that on this one. I've tried 6.10, 7.04, and 7.10. Currently running 7.10 on it. 

It sort of connects to the router, and if you ping the router I get a huge delay between pings, or they don't go through at all. When on the internet, sometimes you can visit one site, but then it goes back to only loading somethings, not others? It just seems to randomly gain connection and lose connection, but Network manager always shows signal strength of 95%. 

I tried to use ndiswrapper, but I couldn't get Ubuntu to stop using the bcm43xx driver. I blacklisted it, but it still loads it for some reason, so therefore ndiswrapper doesn't work right. 

Any suggestions? I know its not the router, or the modem, as it works fine with the other PCs, its something to do with this laptop, the wireless card works fine in Windows, so its not a hardware issue.

---

### Post by wieman01 on 2007-11-30
This is a know issue I think. You need to disable what we call "ipv6". That's a module loaded a boot. So you need to disable it globally (in the kernel) and in Firefox. 

_**Global:**_
[http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6]("http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6")

_**Firefox (see post #12):**_
[http://ubuntuforums.org/showthread.php?t=218733&page=2]("http://ubuntuforums.org/showthread.php?t=218733&page=2")

---

### Post by OhioYJ on 2007-11-30
Thanks for your reply, but I always disable IPv6 right away after I install Ubuntu, I have no idea why its even enabled by default anyways? But IPv6 is in deed disabled.

Any other suggestions?

---

### Post by OhioYJ on 2007-12-01
Still fighting with it. 

How do I completely disable the default Ubuntu bcm43xx driver, when I install NDISWrapper, it always conflicts with the ubuntu driver, even after I blacklist the driver.

---

### Post by scrooge_74 on 2007-12-01
Haven't you try to use the linux driver without ndiswrapper?  It works very well for me

---

### Post by OhioYJ on 2007-12-02
Yeah I tried the Linux driver without Ndiswrapper, which works very well on one of our other laptops, but it doesn't work on this laptop. 

It seems no matter what I do, I still get very inconsistent wireless performance. Sometimes it will work, other times it doesn't, but it always shows that it is connected, with a 92% signal strength.

---

### Post by scrooge_74 on 2007-12-02
DNS servers? I had problems with that in the past?

---

### Post by OhioYJ on 2007-12-02
> DNS servers? I had problems with that in the past?

Thanks for your help so far, but the DNS information is correct, same address I use on all my computers, and this laptop works fine on the wired connection.

I did find it odd though that the link speed said it was 24 mb? Kind of a weird connection speed? Perhaps thats part of the issue, but how do I change that?

---

### Post by OhioYJ on 2007-12-02
Bump.....

---

### Post by OhioYJ on 2007-12-04
Well not sure what I did really, but now it doesn't even see the card? Where can you change the link speed? Maybe that 24 mb is part of the problem?

I think I might try Kbuntu, I know it shouldn't be any different, but what the hey, I'm not getting anywhere with ubuntu at the moment anyways.

---

### Post by scrooge_74 on 2007-12-04
You can also try Debian Lenny, it works for me no more problem for my Broadcom card

---

### Post by OhioYJ on 2007-12-11
Ok I tried Kubuntu, with no luck. 

I re-installed Ubuntu, and tried again with Ndiswrapper, but I can't get the default ubuntu bcm43xx driver disabled.  I blacklisted it but that doesn't do anything.

So I gave up on ndiswrapper and reinstalled bcm43fw-cutter, and the wireless connection sort of works, 93% connection strength, but still a lot of lag time between pings to the router, and then random, periods where it won't talk to the router at all, but it never shows that it loses connection, just acts like it does. I do have link speeds that make sense now though. 

So I'm coming back around to the point of trying ndiswrapper again, but I can't find out how to completely disable that ubuntu bcm43xx driver, black listing it doesn't work, it still loads it. I'm black listing it in /etc/modprobe.d/blacklist .

---

### Post by OhioYJ on 2007-12-11
Ok so once I blacklisted the bcm43xx driver, the wireless card disappears, with no ndiswrapper driver installed.

So it would seem that I have successfully stopped the bcm43xx driver from loading. However, when I install a ndiswrapper driver, why does it always show the driver, then alternate driver bcm43xx, from all the research I've done, the alternate driver part should not be there>?

---

### Post by OhioYJ on 2007-12-12
Bump.....

*crickets*

*crickets*

---

### Post by OhioYJ on 2007-12-12
Ok so I found a script that loads all of the ndiswrapper and stuff for you, and even using that on a fresh install, the ndiswrapper method does not work at all. Even after I installed WICD. If I install the firmware it still reacts the same, where it just randomly does what it wants.

---

