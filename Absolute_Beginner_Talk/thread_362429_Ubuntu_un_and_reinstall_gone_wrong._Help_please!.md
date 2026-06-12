---
title: "Ubuntu un and reinstall gone wrong. Help please!"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by BrewsterPilot on 2007-02-15
Hi!
First of all, I'll just start by saying that I'm a complete computer newbie and I've screwed up.
Phew. That's out.

Anyway, I've been using Windows XP since 2002, enjoyed it OK but I decided to try Ubuntu too, for some fun. Used to Windows XP crashes, I've made the needed System Recovery DVD and as my computer crashed (again) last week, I took the step and downloaded Ubuntu; with the hope of running it in co-existance with XP. Which didn't kind of go as planned...:lolflag: 

So, I press F12 during reboot and choose to reboot from CD/DVD drive (which has Ubuntu 6.06 installer on it). So far so good. Menu screen pops up and I select Install Ubuntu (something like that anyway). When like 95% of the installation is complete a distorted screen pops up saying that I don't have the last version of *X* and tells me to get it @ [http://wiki.x.org/wiki/](http://wiki.x.org/wiki/). Doesn't work. I'm writing this in Graphical Safe mode, which so far has been the only one to work properly.

In short terms, what I want to do is:

-Uninstall and completely empty every bit of my Hard Drive (/C)
-Reinstall Windows XP from the recovery DVD (wont work ATM, says some *failed partition* techno-talk
-Reinstall Ubuntu 6.06 (Hell I love Ubuntu even if it's in Error Safe mode and not working as it should)
-Run both Ubuntu and XP in harmony over the same machine, choosing which to use accordingly as I want.

Is this possible?



Thanks for Your assistance!
BrewsterPilot

---

### Post by kdub432 on 2007-02-15
first, of all,  you need to format your hard drive correctly. I would download a gparted live cd (google it) to wipe your hd and format it with three partitions, a small one for linux swap space, and two larger ones for windows and ubuntu. Then put the windows cd in and install it (provided that its not something from a manufacturer, say a dell restore disk). Then get the latest ubuntu (6.10) and burn a new cd, and install it.....

---

### Post by BrewsterPilot on 2007-02-15
> **kdub432 said:**
> first, of all,  you need to format your hard drive correctly. I would download a gparted live cd (google it) to wipe your hd and format it with three partitions, a small one for linux swap space, and two larger ones for windows and ubuntu. Then put the windows cd in and install it **(provided that its not something from a manufacturer, say a dell restore disk)**. Then get the latest ubuntu (6.10) and burn a new cd, and install it.....

Just to clarify, the recovery DVD, I recorded it after getting my computer (Acer) as the pop/up screen recommended... Will it do?

---

### Post by BrewsterPilot on 2007-02-15
Small problem...
Error Safe mode won't let me extract the Ubuntu installation DVD before I turn the computer off.
How should I now mount the GParted LiveCD iso file to a CD if I can't extract the DVD?

---

