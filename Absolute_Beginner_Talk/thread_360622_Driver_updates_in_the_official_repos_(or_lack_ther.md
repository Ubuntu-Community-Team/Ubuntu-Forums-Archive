---
title: "Driver updates in the official repos (or lack there of)"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Sayne on 2007-02-13
Is there a reason the latest nVidia release (non-beta) drivers aren't in the official repos? Everyone who wants the nVidia drivers wants the latest ones. Is there an issue with the latest 2 or 3 drivers that would stop them from getting put into the repos? It's obviously not a binary only issue since they are there in the first place.

I'm just curious because it's a pain to go get the drivers from nvidia and compile everything, or adding a non-official repo where you have to depend on the maintainer to do it.

So why aren't the latest drivers in the ubuntu repos?

---

### Post by ThrobbingBrain66 on 2007-02-13
I don't have a Nvidia card, so I could be wrong, but the latest drivers are in Feisty.  I think you'll have to rely on someone backporting those drivers into Edgy if you don't want to install them manually.  Backports aren't all that common either, so I wouldn't bet on it.

---

### Post by mendingo84 on 2007-02-13
or you could install the latest beta driver from nvidia using the envy tool, which you will find [here]("http://albertomilone.com/nvidia_scripts1.html"). it'll do the trick as nvidia beta is stable enogh as far as i'm conceirned.

---

### Post by Sayne on 2007-02-13
Does that mean that there will always be only one set of drivers in the repo per Distro version? When Feisty is done, will it only get the drivers once and that's it until the next version as well?

Thanks for the reply, greatly appreciated!

---

### Post by Sayne on 2007-02-13
Yeah I've used Envy for awhile now. But the drivers it gets aren't beta. Those are the latest stable drivers from nvidia, at least their under the stable section of their site. Maybe that's my confusion. Has there not been a stable driver release from nvidia since 87xx?

---

### Post by igknighted on 2007-02-13
there has been at least one stable release since 87xx, and I am almost positive it is in edgy, because apt-get install nvidia-glx always got me the 96xx driver, and I don't remember adding any special repo's.  Now I'm back to my ATI card so its no biggie, but i'm pretty sure the new nvidia driver is there.

BTW, theres no reason to use the beta driver now that 96xx is out, unless you are actually using it for testing, not for home use.

---

### Post by Bachstelze on 2007-02-13
There was a reason to use it when it was 9742 because of the support for newer cards and/or better compositing support (for e.g. Beryl).

But now that 9746 is out, there is no reason to use them anymore, they have been removed from nvidia's website anyway.

---

### Post by Sayne on 2007-02-13
I keep getting the 87xx driver from the repo whenever I used apt to try and get it. Updated before I tried to get it as well. Are you using x86 or amd64? Synaptec also showed the version at 87 as well. Odd...

---

### Post by igknighted on 2007-02-13
> **Sayne said:**
> I keep getting the 87xx driver from the repo whenever I used apt to try and get it. Updated before I tried to get it as well. Are you using x86 or amd64? Synaptec also showed the version at 87 as well. Odd...

I use x86.  Try looking at the beryl how-to's for NVIDIA, as there are some repo's you can add for the drivers if the ubuntu ones dont have it.  It's still easier to do that than install NVIDIA's, and while I suppose a lot of people like envy, I'm very skeptical and would rather do it myself.

---

