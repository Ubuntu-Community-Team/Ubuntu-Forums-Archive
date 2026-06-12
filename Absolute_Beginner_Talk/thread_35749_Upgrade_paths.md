---
title: "Upgrade paths"
date: 2005-05-20
forum: Absolute Beginner Talk
---

### Post by agger on 2005-05-20
The answer to this question may exist somewhere in the online documentation, but I didn't find it anywhere.

I installed hoary about a week ago (after using it for about a week from the LiveCD), and I'm still delighted, though I find problem solving to involve more low-level tweaking than I'm actually used to from WinXP - getting sound and video to work is a bit like making games run under Win95, setting all sorts of things to get the sound right for this game and keeping that game from freezing, etc.

Be that as it may, I'm sufficiently delighted to want to feel committed to Ubuntu: I switched to Linux, and I'd like to trust the Ubuntu distribution to keep up with state of the art.

This means that I'd like to upgrade to Breezy Badger when it's released, and so on. So now my question arrives: 

I'd rather not have to install new releases on an "experimental" partition but take the "plunge" each time. Which means: Are there safe upgrade paths? Is the system guaranteed to work (software and hardware and FS) after an upgrade to a new release, and what impact might upgrading have on 3rd party software - does Canonical have a policy on this?

---

### Post by shof2k on 2005-05-20
In theory each verison is upgradable and this is stated by canonical (ie Warty to Hoary, Hoary to Breezy).  I went from Warty to Hoary and found no probs with 3rd party drives or software packages.  You shouldn't need to do more than 

sudo apt-get update
sudo apt-get dist upgrade

However, since Breezy is still in development, there is a high chance of something not being complete and so making your system unstable.  

On your initial point, I also find linux requires more low-level tweaking than win95.  Whilst it is annoying (and not useful for pure users) it does give us an understanding of the inner workings of our OS.  If you want a linux that doesn't need such tweaking, then linspire or lycoris lead the market there.

---

### Post by Kyral on 2005-05-20
You can upgrade to Breezy now if you want, but take my word for it, its not ready yet. I tried and had to reinstall because Xorg broke

---

