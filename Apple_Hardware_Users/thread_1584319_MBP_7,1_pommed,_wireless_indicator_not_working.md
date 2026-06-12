---
title: "MBP 7,1 pommed, wireless indicator not working"
date: 2010-09-29
forum: Apple Hardware Users
---

### Post by sapi` on 2010-09-29
Hey,

I've been trying to get ubuntu set up as a triple boot on my MBP.  The actual installation goes fine, and I'm writing this from within ubuntu.

However, I can't seem to get the pommed drivers set up, and there's an issue with the wireless.

I've tried following the instructions [here]("https://help.ubuntu.com/community/MacBookPro7-1/Lucid") to set up the keyboard functions, after finding that simply installing mbp-nvidia-bl-dkms, applesmc-dkms, and pommed was not enough to restore functionality.  However, even after following the instructions to build the latest version of pommed, it doesn't seem to be working.  Any ideas on how to get this functionality?

The second issue is more minor, but I can't think of what could be causing it.  I've installed the broadcom STA driver as instructed, and wireless works fine.  However, while I can connect to the internet perfectly, the statusbar wireless indicator is always stuck on disconnected (grey with a red exclamation mark).

I'm testing this on 10.04 x64, but have also tried 10.10 x64 without success.

Any help would be much appreciated.

---

### Post by sapi` on 2010-10-02
As an update, I tried again on 10.10 x64, but still wasn't able to get this working.

Adding the mactel-support ppa didn't get me any of the packages, as they don't seem to be built for maverik; I tried installing the lucid .debs from launchpad but while they install without complaint, none of the keyboard controls work.

I'm sure there's a better way of getting applesmc-dkms / mbp-nvidia-bl-dkms than just trying with old packages, but I'm not sure what it is.  Could someone point me in the right direction for getting a maverik build of those and replacing the lucid one I installed in case that's the problem?

Or if there's any other thoughts on why pommed doesn't seem to be working on the MBP 7,1 that'd be great too?

---

