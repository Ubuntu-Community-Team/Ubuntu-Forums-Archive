---
title: "Power consumption on 12.04"
date: 2012-12-24
forum: Any Other OS
---

### Post by emshains on 2012-12-24
Hello, I am using a derivative of 12.04, elementary OS on a thinkpad X200s. I am running it pretty much stock, except for the SNA driver (the default is DRI). When compared to Linux Mint 11, which was running Gnome 3 with DRI, the battery life was twice as good. Even before I enabled SNA, it still burned through twice as fast. I am curios to know why. Powertop seems to tell me that it is all "good" on 12.04, which was not the case on Mint. This is really troubling, since I need my laptop to be able to do at least 5 hours of office/university programming work throughout the day. I hate to carry around the charger. What can I do to make my battery last longer ? 
I also can't seem to set my CPU frequency to a set state, the governor always tries to run it at the highest possible frequency when it encounters load.

---

### Post by howefield on 2012-12-24
Thread moved to the "*Other OS/Distro Talk*" forum.

---

### Post by BBQdave on 2012-12-24
> **emshains said:**
> This is really troubling, since I need my laptop to be able to do at least 5 hours of office/university programming work throughout the day.

I have a Toshiba Satellite C655, this notebook is rated for a max battery discharge of 5 hours. Though, under normal use - for me, I average 3 hours, than about an hour charge - plug in.

I have used Fedora 17 with Gnome 3, Linux Mint Maya - backported with Cinnamon 1.6, and Ubunut 12.04 LTS with Unity. All average about the same 3 hours of discharge.

Under normal use - which can very depending on applications in use, I think you would be lucky to get 60% of the max battery discharge rate.

---

### Post by montag dp on 2012-12-25
I highly recommend the Jupiter applet. It has done wonders for both of the laptops I've tried it on. My new laptop gets as good battery life on Linux as Windows 7.

---

### Post by memilanuk on 2012-12-25
You do realize the jupiter applet has been recently declared obsolete/deprecated by the upstream maintainer and will eventually go bye-bye unless someone else picks it up?

---

### Post by montag dp on 2012-12-25
> **memilanuk said:**
> You do realize the jupiter applet has been recently declared obsolete/deprecated by the upstream maintainer and will eventually go bye-bye unless someone else picks it up?No I didn't. That's sad. Anyway for now it works well for me.

---

### Post by emshains on 2012-12-26
I have the 9 cell battery on my X200s, it DOES actually last as long as I need. I used to use Jupiter as well, though I thought that it broke some stuff and made my laptop unstable using the latest Ubuntu. I'll try it again. 
Why has this been moved to the Other OS talk, elementary is purely a "skin" of Ubuntu, the only stuff that has changed is the DE, but the kernel and the packages are all the same. And this isn't really an issue with the elementary's "skin", is it?

---

### Post by montag dp on 2012-12-26
With Jupiter going away I think I'm going to download the source code and find out what exactly it does for power savings and then implement it myself, which would allow me to keep it working on my computer even when the OS/kernel change.

emshains, I believe I read that in 12.04 they implemented some power management methods similar to what's in Jupiter (see [here]("https://help.ubuntu.com/community/PowerManagement/ReducedPower")), which may explain why you're getting better battery life on 12.04 than Mint 11.

---

