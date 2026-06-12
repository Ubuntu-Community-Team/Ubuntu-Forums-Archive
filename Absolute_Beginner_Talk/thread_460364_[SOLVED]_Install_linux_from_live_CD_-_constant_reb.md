---
title: "[SOLVED] Install linux from live CD - constant reboots"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-05-31
Hi

I have had Ubuntu 7.04 happily running for a while now. I then decided to play with beryl (I know, my own fault etc) and had it working for a while. Then I decided to do a fresh install, as I felt I had got to grips with most things.

Now when I try to load / restore from the live CD and the alternate CD, I get through the load process (including re-formatting the ubuntu partition), but when GRUB pops up and shows the version of ubuntu I have installed (as well as XP), if I select the ubuntu install, my machine simply reboots and comes back showing the GRUB screen again. This is something I had when I first tried to load ubuntu and I can't remember how I fixed it, although I think it was just by trying a number of different install disks (which I have now done).

Any Clues?

TIA

---

### Post by pappapump on 2007-05-31
Ok so if I get this right, on your os choices menu you still have the option to boot into XP?
If so, then you should go to XP and do a quick scandisk and defrag and try again.
Remember that linux isn't XP compatible and if you decide to try to load it over a partition that XP has control you may have some problems.
So, try this.
Once you boot into XP try your Administration window and storage manager and choose the disk management program.
Then see if your ubuntu partition is visible from there.
If it is choose to delete the partition, then reboot and the live CD will be able to take it from there.
When presented with options during Ubuntu install make sure you choose to use the un-partitioned space on the existing hard drive and all should be well.

---

### Post by ubername on 2007-06-01
> **pappapump said:**
> Ok so if I get this right, on your os choices menu you still have the option to boot into XP?
If so, then you should go to XP and do a quick scandisk and defrag and try again.
Remember that linux isn't XP compatible and if you decide to try to load it over a partition that XP has control you may have some problems.
So, try this.
Once you boot into XP try your Administration window and storage manager and choose the disk management program.
Then see if your ubuntu partition is visible from there.
If it is choose to delete the partition, then reboot and the live CD will be able to take it from there.
When presented with options during Ubuntu install make sure you choose to use the un-partitioned space on the existing hard drive and all should be well.

Thanks

Trying that now

---

