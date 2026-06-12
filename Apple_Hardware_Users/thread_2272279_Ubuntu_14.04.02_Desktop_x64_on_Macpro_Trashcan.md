---
title: "Ubuntu 14.04.02 Desktop x64 on Macpro Trashcan"
date: 2015-04-05
forum: Apple Hardware Users
---

### Post by oxsyn on 2015-04-05
Work gave me a brand new trashcan, 64GB ddr3, 1TB SSD, promise thunderbolt raid.
I'm attempting to install Ubuntu 14.04.02 Desktop x64 on it using the instructions from here: [https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro).
I installed the latest version of REFind, booted the installer media using the instructions, ran the installer - deleted all partitions except EFI, created 64GB swap & used the rest for root (super simple, just want to make sure it works).

I've run the installer several times now, each time it gets stuck at the same point: "Preparing language-pack-gnome-en-base (amd64)". Any suggestions?

---

### Post by este.el.paz on 2015-04-06
> **oxsyn said:**
> Work gave me a brand new trashcan, 64GB ddr3, 1TB SSD, promise thunderbolt raid.
I'm attempting to install Ubuntu 14.04.02 Desktop x64 on it using the instructions from here: [https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro).
I installed the latest version of REFind, booted the installer media using the instructions, ran the installer - deleted all partitions except EFI, created 64GB swap & used the rest for root (super simple, just want to make sure it works).

I've run the installer several times now, each time it gets stuck at the same point: "Preparing language-pack-gnome-en-base (amd64)". Any suggestions?

Those instructions look fairly complicated . . . the general wisdom seems to be to do "dual boot" . . . i.e., keep OSX and create another disk formatted as "free space" for linux and try to run the install as "install next to" and see if the installer can finish the install that way.  It looks like the installer is "crashing" . . . the exact place may or may not be relevant to outcomes.  But, first question I ask all the folks having trouble installing is . . . did you check the mdsum number?  And, then, did you burn the DVD at "slowest speed" setting?  If the number doesn't match, try to download another iso and try again . . . .

e...

---

