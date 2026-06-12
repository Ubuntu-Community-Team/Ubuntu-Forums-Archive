---
title: "Installed 10.04 on a PPC G4 Albook. Blank screen on OF boot."
date: 2012-05-24
forum: Apple Hardware Users
---

### Post by killsurfcity on 2012-05-24
Hi, I'm both a forum noob and an ubuntu/linux noob, so, be gentle, haha.

I've been trying to install varieties of ubuntu for the past couple days, and ubuntu 10.4 finally worked. I had to boot with... ```
boot cd:,\\:tbxi
```

...but it booted fine, and the installer ran as expected. Reboot however failed. The machine hung on shutdown, displaying a partially grayed out screen with the OF command line visible in the background, though non-functional of course.

At this point, boot attempts go like so...
Regular start button boot: I hear the Apple chime (that's odd right?), see the OF command line, and it hangs at "returning from prom_init".

OF boot using "boot": I again, hear the Apple chime, get the OF prompts, then enter only "boot". The screen sort of flickers, I see the typical startup sequence, proceed through Quiesce, the screen flickers again as if it's going to load the splash, but it just hangs with a black screen indefinitely.

Hope all of this info helps. My machine is a G4 Albook 1.67ghz: [http://www.everymac.com/systems/apple/powerbook_g4/specs/powerbook_g4_1.67_15.html](http://www.everymac.com/systems/apple/powerbook_g4/specs/powerbook_g4_1.67_15.html)

Thanks in advance for the help!

---

### Post by killsurfcity on 2012-05-25
I guess it's either to MintPPC or back to Os X for me then. It seems like the more I google the more I realize my 5,6 PB is a nightmare on ubuntu. Shame, it looked pretty nice.

---

### Post by rsavage on 2012-05-25
> **killsurfcity said:**
>  It seems like the more I google
 
That's your first mistake there. Why don't you try read the PowerPC documentation?

---

### Post by killsurfcity on 2012-05-25
Not to be a contrarian, but why bother, when a quick search reveals innumerable threads and blogs where people with a real proficiency in Linux can't seem to get their Powerbook 5,6 machines working properly? 

What could I possibly be missing? Either someone here is going to tell me it's possible to get this thing running, or not. 

One of the issues I didn't realize before I installed, is that the 5,6 PB's are quite different from the iBooks and TiBooks a lot of people have working under ubuntu. SO any info about those machines is effectively useless to me.

Also, I really just wanted to install an OS and be done with it, not learn a new programming language. So if ubuntu can work, but only after 2 weeks of editing .conf files, i'm not interested. I figured this would be relatively simple, like hackint0sh builds. Yeah, maybe you spend an hour in terminal, so what? But it looks like people hack away on this Linux stuff endlessly and settle for sub-par results. (on mac at least) If this is not the case, please enlighten me, because that sure is how it seems.

Thanks!

---

### Post by rsavage on 2012-05-25
> **killsurfcity said:**
> Not to be a contrarian, but why bother, when a quick search reveals innumerable threads and blogs where people with a real proficiency in Linux can't seem to get their Powerbook 5,6 machines working properly? 

A great deal of effort has gone into making PowerPC *ubuntu work.  Where things do not work out-the-box it is backed up by thorough documentation.  A huge amount of time has gone into making the process as easy as possible for people.  If that documentation doesn't work for your machine then we need to know, but it is hard to help you when you don't want to help yourself.  
 
Please provide the links for these blogs and threads by supposed proficient people.
 
I know it is possible to get your exact machine working without learning "a new programming language".

---

### Post by killsurfcity on 2012-05-25
Perhaps. Maybe I'm just a bit lost in the way things are documented. Seems to be a lot of "in the weeds" talk and very little; "If this is your build, this is what you run. These are common issues, here's how they are fixed." However, maybe I'm looking in the wrong place. All I know is installing a Linux distro on this machine has been seemingly unending frustration and misdirection.

Now that that's out of the way, here's where I am...

I decided to give lubuntu another shot. Live CD runs fine, though, no wifi of course. Installed great, but like ubuntu, failed to quit afterwards. I re-booted, and it loaded up fine. It seems ok, at least no glaring problems, but I'd like to get wi-fi working. Can't seem to find any information about that in the Lubuntu documentation.  Perhaps you can point me in the right direction?

---

### Post by rsavage on 2012-05-25
> **killsurfcity said:**
> 
Can't seem to find any information about that in the Lubuntu documentation. Perhaps you can point me in the right direction?
 
Then you can edit their wiki and provide the PowerPC links. Lubuntu and indeed PowerPC is community supported.  If you don't get involved in improving documentation then you have no right to moan about it.
 
The PowerPC documentation is linked in the first post of the sticky thread "Where to download Ubuntu for PowerPC and other frequently asked questions "

---

### Post by killsurfcity on 2012-05-25
I'll be sure to report if I get anything working, but I don't know how that's supposed to help me do anything now.

So after resorting to more googling, if found a terminal command that returns my wireless card details. Seems I need a driver for a BCM4306. How do I obtain one? (Yes, I looked)

---

### Post by rsavage on 2012-05-25
.......... [https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F](https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F)

---

