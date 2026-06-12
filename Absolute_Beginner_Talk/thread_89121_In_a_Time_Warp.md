---
title: "In a Time Warp"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by Drifter on 2005-11-11
I had a clock problem where xp's clock would run fast by 5 to 7 hous after booting in ubuntu, ubuntu's clock was ok.  I then tried this:

sudo update-rc.d -f ntpdate remove  Now xp's clock is ok,but unbuntu's then is slow by about 5 hours if I boot from xp to ubuntu.  I have two harddrives.  Anyone know what to do to fix this so both will work.

---

### Post by apjone on 2005-11-11
check your timezones as ubuntu saves time to hardware on shutdown and picks it up from there at start-up

---

