---
title: "Make it run cooler?"
date: 2009-07-28
forum: Apple Hardware Users
---

### Post by Tofuik on 2009-07-28
Using a MBP 4,1

Is there anyway to make ubuntu run cooler?  I've got my fans working but I can only pretty much have them max or default 2000rpm.  The fans never work well enough IMO, even with the stupid apple firmware update I still have to run smc fan controller to get the fans to kick up higher when I'm doing videoediting, gaming, virtualmachines, etc.  Its like apple doesn't want its pro users to reproduce in the future.

I really want to get a linux distro working properly that runs just as cool, if not cooler than OSX.  I know that the macs run hot in general and I wish there was a way to combat this. I've also tried getting my battery life longer as well (up to around 3 hours now) but its no where near the 5 I can get in OSX.

I know osx is meant for the mac and there for runs much better because it was designed for that hardware, but my old HP laptop never ran hot with Linux, it always ran cooler than with xp.

Ubuntu runs great, just hot.  I'm starting to wonder if I should just look for a lighter distro (been staring at OpenSUSE cause alot of people claim its good on laptops) or start to strip down ubuntu so its lighter.

---

### Post by Whiffle on 2009-07-28
Is CPU scaling working correctly?  I'm not real familiar with macs, but that would be something I'd check into on any laptop.

---

### Post by Tofuik on 2009-07-28
> **Whiffle said:**
> Is CPU scaling working correctly?  I'm not real familiar with macs, but that would be something I'd check into on any laptop.

Not sure actually.  I got my friend to dig around and we adjusted alot of settings which is why I get 3 hours of battery now instead of 2.

---

### Post by hvthao on 2009-07-28
Normally in my macbook pro, I set the fan_min 3500rpm to make it cool like in OSX. And to increase the battery life, trying some scripts that you can find in this Apple Users forum or using the laptop-mode utility. Macbooks 4,1 use 58Wh battery, larger than the macbook pro 13in. However, you cannot get 6 or 7 hours because macbook pros uses P cpus instead of T cpus.

---

### Post by Tofuik on 2009-07-28
> **hvthao said:**
> Normally in my macbook pro, I set the fan_min 3500rpm to make it cool like in OSX. And to increase the battery life, trying some scripts that you can find in this Apple Users forum or using the laptop-mode utility. Macbooks 4,1 use 58Wh battery, larger than the macbook pro 13in. However, you cannot get 6 or 7 hours because macbook pros uses P cpus instead of T cpus.

I'll look into this.  As for the 3500rpm setting, I've noticed that that seems to be the best setting in a lot of situations.  Just listening to music and browsing the internet has me at 54C if I don't bump it up.

---

### Post by galuzyaki on 2010-04-26
3500rpm setting is optimal

---

### Post by xxander on 2010-04-26
How do you make your computer run at 3500 rpm? (in Linux and OS X)

---

### Post by v1ad on 2010-04-26
if we are talking fan speeds, shouldn't u be looking in the bios. never heard of an operating system controlling the fans. 

your computer does not run are 3500 rpm, only your fans do. and they change depending on the temperature of the cpu or the whole laptop. check your bios settings you should be able to control it from there.

---

### Post by xxander on 2010-04-26
MacBooks don't have Bios files, just EFI... how can we mac users do this?

---

### Post by v1ad on 2010-04-26
O Mac :[ my bad. think they have an app for it but it could be for their operating system only.

---

### Post by xxander on 2010-04-26
Haha.  Oh well... I'll just spend some time "googling" i guess.

---

### Post by llamabr on 2010-04-26
What machine are you running?  On my ibook, i switched from ubuntu to debian lenny.  Since ubuntu no longer supports the ppc architecture, I found more and more things going bad but no one wanting to fix them.  It solved my over heating problem, and a few others, too.

---

### Post by xxander on 2010-04-27
I have an Intel MacBook3,1.

---

