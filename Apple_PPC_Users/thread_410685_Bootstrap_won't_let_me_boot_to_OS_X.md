---
title: "Bootstrap won't let me boot to OS X"
date: 2007-04-16
forum: Apple PPC Users
---

### Post by KBCraig on 2007-04-16
Total *nix newbie here (except for faking it by running MacOS X since the first Public Beta). I was intrigued by some friends discussing Ubuntu, and thought I might try it to get better performance on my aging Mac. I've used MS-DOS/Windows since the mid-'80s for work, and MacOS since '89 by personal preference at home. I'm willing to get my hands dirty learning new stuff, but this is uncharted territory for me.

Hardware: B&W G3/350 upgraded to G4/733; MacOS X 10.2.8 is on the 120GB Seagate master, and Ubuntu 6.10 on the 20GB Maxtor slave.

I downloaded and burned the Ubuntu 6.10 Live CD. Played with it for a couple of days, and decided to give it a try on an unused internal HD. I trusted the installer, and let it erase and reformat the target drive (the 20GB Maxtor).

Okay, Ubuntu is fun and slightly faster on this machine, but the lack of Flash/Shockwave support sure hurts my Web browsing. 

So, I try to boot back into MacOS X, but no luck. When I select "x", Bootstrap says that my file/partition is not found, and boots into Ubuntu. I've tried rebooting while holding each of the alt/option/ctrl keys, but no luck. Bootstrap still loads, and still can't find my OS X disk.

Thanks for any help. Please speak slowly if you use big words. Assume I know nothing about Terminal commands.

Kevin

---

### Post by pxwpxw on 2007-04-16
Hi,

Try holding down Option key at start up again, should bring up a graphical boot selection, if not, next suggestion.

---

### Post by KBCraig on 2007-04-16
I don't know what was different this time from the dozen previous attempts, but I was finally able to boot into OS X.

I powered off completely, then powered on and held the Option ("Windows 'start'") key. At the first stage of bootstrap, I entered "x", and it switched to booting OS X.

The *only* thing I did that I hadn't done before, was to power down instead of choosing "restart".

I'll play more with Ubuntu, but for now it's nice to have my Mac back.

---

