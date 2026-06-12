---
title: "SD MMC drivers"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by compennex on 2007-07-19
i have a SD Memory card slot on my laptop, but i have no idea on where to find a driver for it and how to install it. maybe im just not lookin hard enough or somethin

---

### Post by dptxp on 2007-07-19
I am sure that you have ENE card reader.
Sorry, no solution yet.

You can make sd card work if you have TI card reader.

---

### Post by tama on 2007-07-20
There's actually a patch against 2.6.20 [here]("http://list.drzeus.cx/pipermail/sdhci-devel/2007-May/001735.html") which should solve the issue.
It's been pushed into mainline kernel after the 2.6.22 release [here]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=7de064ebc67d9baf6c933d3a7046feb9b4eced05;hp=98ccf14909ba02a41c5925b0b2c92aeeef23d3b9#patch1").
And there's a [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/62995") discussing this too.

Now, I wonder if this patch will land into Gutsy. I'd really love the SD reader working out of the box for Gutsy :)

---

### Post by CrownP10:8 on 2007-07-22
Very glad to hear of this fix going into the kernel packages, I'm running the Ubuntu Studio low latency kernel for audio, so recompiling for this patch might be more tricky than it's worth. Until then I will make do with a cheap USB card reader, or reboot to Windows :lolflag:

---

### Post by compennex on 2007-07-26
> **tama said:**
> There's actually a patch against 2.6.20 [here]("http://list.drzeus.cx/pipermail/sdhci-devel/2007-May/001735.html") which should solve the issue.
It's been pushed into mainline kernel after the 2.6.22 release [here]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=7de064ebc67d9baf6c933d3a7046feb9b4eced05;hp=98ccf14909ba02a41c5925b0b2c92aeeef23d3b9#patch1").
And there's a [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/62995") discussing this too.

Now, I wonder if this patch will land into Gutsy. I'd really love the SD reader working out of the box for Gutsy :)

i checked this kernel out, but i have no idea what to do with it :confused:

---

