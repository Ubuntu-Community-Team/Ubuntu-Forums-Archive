---
title: "Core2Duo and Ubuntu 7.04"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-10-10
I've just upgraded my computer to a C2D 2.33Ghz PC, and have a question on the Ubuntu install. I had Ubuntu running quite successfully on my previous machine, a Celeron 2.8Ghz, and have uninstalled and re-installed a few times, so am used to the process.

I think I recall seeing a post regarding a separate edition of Feisty Fawn for dual processor machines. Could anyone enlighten me if this is so, as to what differences this might cause when I instal Ubuntu on the new machine. I think there's a separate distribution for C2D machines - would this be so?

Any comments/advice greatly appreciated.

---

### Post by rsambuca on 2007-10-10
You may as well use the 64bit version to take full advantage of the new processor.

---

### Post by jimrz on 2007-10-10
> **corowakid said:**
> I've just upgraded my computer to a C2D 2.33Ghz PC, and have a question on the Ubuntu install. I had Ubuntu running quite successfully on my previous machine, a Celeron 2.8Ghz, and have uninstalled and re-installed a few times, so am used to the process.

I think I recall seeing a post regarding a separate edition of Feisty Fawn for dual processor machines. Could anyone enlighten me if this is so, as to what differences this might cause when I instal Ubuntu on the new machine. I think there's a separate distribution for C2D machines - would this be so?

Any comments/advice greatly appreciated.

no need for different ver. my c2d E6600 works great and fast (completes super pi20 in < 16 sec.) on 7.04 using the generic kernel. both procs are recognized and the workload seems to be split about right. you could go with the 64 bit ver, but it brings some issues with it that are not there on the 32-bit. unless you have some need foe 64 bit, and there are currently very few apps available that can utilize it, stick with the 32 bit as there is little or no performance gain with normal apps using the 64

---

### Post by rsambuca on 2007-10-10
> **jimrz said:**
> no need for different ver. my c2d E6600 works great and fast (completes super pi20 in < 16 sec.) on 7.04 using the generic kernel. both procs are recognized and the workload seems to be split about right. you could go with the 64 bit ver, but it brings some issues with it that are not there on the 32-bit. unless you have some need foe 64 bit, and there are currently very few apps available that can utilize it, stick with the 32 bit as there is little or no performance gain with normal apps using the 64
This post is 100% INCORRECT, and based on stale, out-dated information.  You can get performance gains upwards of 30%, and the number of package differences between the 32bit and 64bit repositories is less than 1%.  Please don't make your decision based on this outdated FUD.

---

### Post by misfitpierce on 2007-10-10
64 is a great speed enhancement and can run 32 bit and 64 but app's for deb. I would go 64 bit. Only thing you may hit is flash issue search for 64 bit ubuntu flash script for it to auto install flash into your firefox using ndiswrapper.

---

### Post by Paqman on 2007-10-10
> **jimrz said:**
> there are currently very few apps available that can utilize it

This is total, utter tosh.

---

### Post by steveneddy on 2007-10-10
I just went 64 bit on a Core 2 Duo (2 Ghz) with 2 Gig RAM and I wouldn't go back to 32 bit unless 64 bit suddenly disappeared.

Run 64 bit and the world gets much happier.

Check out the 64 bit forums, DL or get somehow, a 64 bit version and install it.

Video and sound are MUCH improved and performance is snappy and crisp.

Why run 32 bit software on a 64 bit machine?

:popcorn:

---

### Post by HackCoders on 2007-10-10
Is there a release for 64 bit Gutsy anywhere? I'm downloading it now from my ISP's website, it's like 700mb but NONE of the ones featured there said if its 32 or 64bit...

---

### Post by rsambuca on 2007-10-10
> **HackCoders said:**
> Is there a release for 64 bit Gutsy anywhere? I'm downloading it now from my ISP's website, it's like 700mb but NONE of the ones featured there said if its 32 or 64bit...

You can get the [64bit daily build of Gutsy here]("http://cdimage.ubuntu.com/daily-live/current/").  Just so you know it is still beta version.

---

### Post by Paqman on 2007-10-10
> **HackCoders said:**
> NONE of the ones featured there said if its 32 or 64bit...

Check the name of the file you're downloading

32bit = i386
64bit = amd64

---

### Post by HackCoders on 2007-10-10
Does amd64 one work on core 2?

---

### Post by rsambuca on 2007-10-10
Yes.  That is the one you want.

---

### Post by Frak on 2007-10-10
> **HackCoders said:**
> Does amd64 one work on core 2?
Yes, amd64 is just a universal name for x86_64 (your processor)

It should run somewhat faster than its 32-bit counterpart. Render way faster.

---

### Post by HackCoders on 2007-10-10
Thanks for that ^_^

---

### Post by HackCoders on 2007-10-10
lol it's 4.5GB, guh I don't have an empty DVD disc :(

---

### Post by rsambuca on 2007-10-10
Did you go to the link I gave you?  It is 697MB.

---

### Post by HackCoders on 2007-10-10
Yeah :)

Thanks for that, well I've asked my ISP to mirror it, they had it on their server like an hour ago, I don't know where it went :(

Gotta get it off them so the download doesn't count towards my bandwidth limit..It'll be a few hours before they mirror it :(

---

### Post by corowakid on 2007-10-11
Thanks all, I'll go the 64bit route - probably wait until Gutsy Gibbon is released (19/10, right?).

---

### Post by Joeb454 on 2007-10-11
No it's the 18th so you get it a day earlier than you expected!! :)

---

### Post by nonewmsgs on 2007-10-11
> **HackCoders said:**
> Yeah :)

Thanks for that, well I've asked my ISP to mirror it, they had it on their server like an hour ago, I don't know where it went :(

Gotta get it off them so the download doesn't count towards my bandwidth limit..It'll be a few hours before they mirror it :(

they count your downloading for bandwidth?  oh my.  i dont tell my isp so they dont even know how much i download, it's a secret.:-$

edit: and the 64bit rulez.

---

