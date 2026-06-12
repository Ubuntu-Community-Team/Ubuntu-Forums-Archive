---
title: "Screwed up graphics drivers"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by darkness5723 on 2007-09-30
Okay this is a bit of a weird situation. I was playing around trying to run compiz fusion the best way (got everything working alright now) but in the process I installed and uninstalled the proprietary drivers. No biggie normally, except for some reason the drivers didn't revert to the xorg drivers. So... screwed up X window happened, I used sudo dpkg -reconfigure xserver-xorg. Worked fine for resetting the drivers and all.  Got compiz fusion working perfectly (as perfectly as it can anyway).

BUT.. the problem is somehow my resolution is stuck at 1080 x 764 or lower and the graphics are kinda grainy. I tried reconfiguring again to see if itd let me select a higher resolution, but it won't. Is it possible to manually edit xorg.conf to force resolutions? or is there some other way to do this.

---

### Post by overdrank on 2007-10-01
> **darkness5723 said:**
> Okay this is a bit of a weird situation. I was playing around trying to run compiz fusion the best way (got everything working alright now) but in the process I installed and uninstalled the proprietary drivers. No biggie normally, except for some reason the drivers didn't revert to the xorg drivers. So... screwed up X window happened, I used sudo dpkg -reconfigure xserver-xorg. Worked fine for resetting the drivers and all.  Got compiz fusion working perfectly (as perfectly as it can anyway).

BUT.. the problem is somehow my resolution is stuck at 1080 x 764 or lower and the graphics are kinda grainy. I tried reconfiguring again to see if itd let me select a higher resolution, but it won't. Is it possible to manually edit xorg.conf to force resolutions? or is there some other way to do this.

Hi I believe this link will help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Good luck! :KS

---

### Post by darkness5723 on 2007-10-01
Thanks :)...
*slap head* cant believe I didn't think to look in the docs.. lol.

I'll read through everything and hopefully that'll work.. small resolutions annoy me

Thanks again

---

