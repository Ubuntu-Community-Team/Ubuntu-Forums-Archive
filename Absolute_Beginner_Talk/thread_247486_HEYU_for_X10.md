---
title: "HEYU for X10"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by tydaking on 2006-08-30
Has anyone been able to install the HEYU program or one similar to allow use and control of X10 modules?

---

### Post by Coombabah on 2006-11-07
Installed heyu-2.0beta.6.2 last night into edgy and had it controlling my x10 lights via a CM12AU module (Australian version) :)

---

### Post by complexicated on 2006-12-04
I must be missing something.. brand new ubuntu user. Is there a package available for download? When I try to compile I get the following error: 

date.c:20:19: error: stdio.h: No such file or directory
date.c:21:18: error: time.h: No such file or directory
date.c:23:20: error: unistd.h: No such file or directory
date.c:25:23: error: sys/types.h: No such file or directory
date.c:28:23: error: sys/param.h: No such file or directory


Seems to me like those libs should automatically be found..

Thanks,
  newbie

---

### Post by gjtoth on 2006-12-04
I got it installed and running.  I *DID* have some weird errors though.  Turns out there was a couple of bugs in Heyu.  Charles Sullivan (the author) has released a new version.  D/l it and try compiling.  If you're still having a problem, contact Charles.  He's exceptionally good at figuring out what the problem is and providing a solution... even if it means changing a little code around for you.

After looking at your errors, I note (if I recall correctly) that those were the errors I received.  Try the new version from Charles.

---

### Post by steevc on 2006-12-04
I did run HEYU on Dapper a while back to test my X10, but I don't remember having any serious issues with it.

I was trying to work out why the X10 units had stopped responding to signals from my Comfort (alarm/home control system). It turned out that our new hair dryer was blocking the signal if it was left plugged in near the Comfort.

I could be tempted to do more X10 stuff with the PC, but I don't leave it on all the time and also my CM12 gets a bit warmer than I like.

---

### Post by gjtoth on 2006-12-04
> **steevc said:**
> I did run HEYU on Dapper a while back to test my X10, but I don't remember having any serious issues with it.

I was trying to work out why the X10 units had stopped responding to signals from my Comfort (alarm/home control system). It turned out that our new hair dryer was blocking the signal if it was left plugged in near the Comfort.

I could be tempted to do more X10 stuff with the PC, but I don't leave it on all the time and also my CM12 gets a bit warmer than I like.

Pick up a CM11A then... You can pick 'em up on eBay dirt cheap.

---

### Post by complexicated on 2006-12-04
Figured it out.. Just need to install the "build-essential" package.. you would think if you had a compiler installed this would be installed also.

---

### Post by mrklaw on 2006-12-13
> **complexicated said:**
> Figured it out.. Just need to install the "build-essential" package.. you would think if you had a compiler installed this would be installed also.

Thanks for this. I just got it working on Edgy after installing the "build-essential" package. Working great!

---

