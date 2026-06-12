---
title: "PowerPC Support"
date: 2007-10-23
forum: Apple PPC Users
---

### Post by Aifel on 2007-10-23
I am considering install Gutsy on my Mac, but I am wondering if the PowerPC support is any good.

---

### Post by FredB on 2007-10-23
PowerPC is not officially supported. So, I don't know if it is really a good idea.

---

### Post by grazie on 2007-10-23
It really depends upon what your expectations are. Now that Canonical no longer officially support the platform, you are not going to get any where near the level of support you can expect from x86. If you're happy to wait a little and contribute what you can to the community you may well enjoy the experience. Note also that Dapper is still officially supported, although it's no longer as up to date as the newer builds. Also, Edgy and Feisty will have fewer problems than Gutsy, which has only just been released.

If you want PowerPC Linux that is officially supported by the distro I think your only alternatives are Debian, Gentoo (source based) and YDL (restricted free support). Ubuntu for PowerPC still has a lot to offer.

---

### Post by Aifel on 2007-10-23
Well, Ubuntu has always been my distro of choice, and I can't stand the slowness of RPM distros... Oh well.

---

### Post by Abandon on 2007-10-23
> **grazie said:**
> If you want PowerPC Linux that is officially supported by the distro I think your only alternatives are Debian, Gentoo (source based) and YDL (restricted free support)..

And OpenSuse 10.3 has an excellent PPC version (DVD) available. 

> **grazie said:**
> Ubuntu for PowerPC still has a lot to offer.

Nope, not for Gutsy at this time. There is also something wrong with the iso,it is way to small and I don't get it to work. Pitty!

---

### Post by czechman86 on 2007-10-23
i use to run 7.04 on my powerbook and it worked great, however there are quite a few things that will not work. from what ive read ubuntu on ppc may not be the best option at this time though, what with that iso problem and what not.

good luck!

---

### Post by grazie on 2007-10-23
> **Abandon said:**
> And OpenSuse 10.3 has an excellent PPC version (DVD) available.
It was my understanding that PPC Suse/OpenSuse wasn't officially supported, but that appears to be incorrect. In that past I've found Suse to be bloated & slow, and the relationship with Novell and hence M$ to be less than ideal. Nonetheless, I'm just downloading the network boot image to give it a whirl. That way I hope I'll be able configure it to be a lot lighter than standard. We'll see.

---

### Post by Aifel on 2007-10-23
I've also never found OpenSuSE to be that good as well. Too Windows-ish. So it basically narrows down to YDL, OpenSuSE, Ubuntu 7.04, Debian and Gentoo... Darn.
Just to clarify what I'd like out of a system: my printer hopefully works (which is why I'd like Gutsy), my nVidia GeForce FX Go5200 to work well, and Cedega support. Which is unlikely to work on a PPC computer...

---

### Post by Caraibes on 2007-10-23
forget Gutsy for PPC, it sucks so much that it hurts... Go directly for the Dapper alternate install cd. It works fine on my G3 iBook.

---

### Post by sulobanks on 2007-10-24
I would go for debian testing.  That 'testing' is not as ominous as it sounds and is probably more stable than feisty.  It's just not as bleeding edge as gutsy.  But at least it's not bleeding.  I really wanted to come back to ubuntu because it's been so polished in the past, and I still use ubuntu on all my x86 machines.  But I haven't seen a release of ubuntu that works on my ibook g4 correctly since edgy.  It might be a good idea for the ppc team to bump ppc releases back a month or two.  Let them lag behind the official releases.  Without official support, I would imagine it's not as easy to get things done as before.  They were putting out fantastic releases before that.  Maybe a little extra time on each release would make the difference.

---

### Post by dynamicv on 2007-10-24
For those installing from scratch, try installing the Alternative Feisty build then allowing Update Manager to apply the 7.10 updates once you've got a working 7.04 system.

I'm having absolutely no problems with Gutsy for PPC on my PowerBook.  Some aspects appear to be more stable, for example the later build of wpa_supplicant no longer drops the connection.

---

### Post by prairie_dad on 2007-10-24
Fedora also has official ppc support, I do believe.  And gentoo doesn't have any "official" anything, really, it's the purest community support I've ever seen, and the best.  I know people poo-poo gentoo for it's "complexity," and yes it's a pain in the butt to have to compile everything (virtually) from scratch, but...

having put it and various -buntus and fedora and slackware on a dozen or so ppcs and x86s, i must say I think Gentoo is the best supported, fastest and most intelligent linux of them all.  Really.  the community is awesome, really helpful, and, even more important, the documentation on their website is absolutely, positively without equal...nothing else comes close.  you don't have to know what you're doing (which is what people always use as an excuse not to use it) just follow the very explicit directions and you are going to be thrilled.  

I know I am happier updating it than I am trying to do this teensy little upgrade from feisty to gutsy.

---

### Post by mokawi on 2007-12-04
My powermac G4 would not boot under Feisty, so I switched to Fedora 6.
The sound driver for the original sound was a little better, as the quality was much better than Edgy's, but it still crashes from time to time, especially when there's a lot of network traffic (there is no patch for the moment). On the other hand, I've had trouble using my external hard drive on firewire, even with the new drivers.
There's also a bug that prevents me from using glx. As with Ubuntu, fan control is sketchy and so is energy management.
Overall fedora 6 was already a lightweight distro, hence pretty fast and well adapted to this old machine. F7 and F8 tremendously improved the boot time. They are simple to use, but maybe not newbie-simple. On the other hand, I wouldn't say that of Ubuntu-ppc either; there's way too much fine-tuning necessary.
Fedora began supporting ppc in 2005, when Apple was switching to x86, so they're probably in the picture for some time.

BSDs have ppc versions too. How do they rate?

---

### Post by stmiller on 2007-12-06
Ubuntu dropped commercial paid tech support for PowerPC. PowerPC releases are still made for Ubuntu, with packages, updates, and everything like x86 Ubuntu. 

The support is here on the user forums. This is the same for any other Linux distro: Fedora, Suse, Gentoo, Debian, etc. When you need support you go to a forum.

So PowerPC Ubuntu is "supported" just as well as all of the other distros.

Feisty was a rock solid release. The Gutsy discs have a problem booting, though there is a [quick fix]("https://wiki.ubuntu.com/PowerPCKnownIssues"). Gutsy has a wealth of improvements for airport extreme, newer version of gnash for youtube, and a newer kernel of course that supports more devices. And newer Gnome/KDE of course.

People often recommend releases that are a year or more old, but I would personally not run anything before Feisty.

---

