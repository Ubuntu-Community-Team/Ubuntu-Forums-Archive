---
title: "OS X Will Not Boot (Possible rEFIt problem)"
date: 2009-03-09
forum: Apple Hardware Users
---

### Post by cubeman on 2009-03-09
I posted this over on Apple's Support Forums, and I just wanted to see if anyone had any input here.

Some computer info before you read:
MacBook Pro from late 2007 (Dual-Core 2.0 GHz, 2 GB RAM)
Dual Booted with Latest Leopard and Ubuntu Linux
I use rEFIt as my boot menu

So this happened the other day: I had just restarted OS X, and I noticed that the process "CrashReport" was eating up about 80% of my CPU. I figured it might have a window open somewhere. I searched, but no dice. I decided to kill it via Terminal. Once I stopped the process it came back with a different process ID. Same thing happened with another try. So I just decided to reboot. That's when it happened -- OS X would not load.

It gets stuck at the Apple Logo with the turning wheel. Rebooting does not help. I attempted to boot into SUM as well as put it in TDM, but neither work. With those not working I tried the Leopard Install CD. My harddrive shows up but my partition table does not. This is where it gets annoying: I can still boot into Linux AND mount my OS X partition. I have no idea why this is happening. As far as I can reason I think it might be my boot menu. I can disable it via SUM if I could get to it. Any ideas? I'm probably missing a very simple fix.

And no I cannot mount my OS X partition under Ubuntu in writable mode -- it disagrees with HFS+ journaling. (That fix requires me to boot into OS X :-P)

Thanks for any feedback.

---

### Post by cyberdork33 on 2009-03-09
It sounds like your partition tables are messed up. There is a partition tool in the refit menu. Does it say your tables are out of sync? 

Your best option might be to boot Ubuntu, back things up, and reinstall OSX.

---

### Post by cubeman on 2009-03-09
Yep, I've ran the rEFIt partition tool, says it's all okay.

The thing about reformatting is that I'd have to remove both OSes since they won't show up under an install CD. I have a few more disk utilities that I need to dig up and try.

---

### Post by cyberdork33 on 2009-03-11
> **cubeman said:**
> The thing about reformatting is that I'd have to remove both OSes since they won't show up under an install CD. I have a few more disk utilities that I need to dig up and try. that is why I'd say that you have a partition table problem.

---

### Post by cubeman on 2009-03-11
Thanks for your input cyberdork. I managed to set everything straight using TestDisk.

---

