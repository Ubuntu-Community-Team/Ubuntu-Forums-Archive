---
title: "Wattage measured on PPC G5 iMac"
date: 2008-05-13
forum: Apple Hardware Users
---

### Post by stream303 on 2008-05-13
I thought I'd actually measure the wattage usage of my G5 iMac.  I picked up a P3 International "Kill A Watt(tm)" meter and put it to the test.

At idle, using the default Ubuntu powernowd scaler, the system at idle consumes around 98 watts.  With a lot of disk activity, this goes up to about 121 watts.

Problem is, powernowd never seems to scale the system back down at all.  I thought that maybe it was allowing the system to "race to idle" to save power, but it doesn't appear to.

So, I uninstalled powernowd, and used cpudyn as the scaler.  Sure enough, it does scale back down to half my max freq to 900mhz, but does it save power?

Yes - with the system idling, and cpudyn backing my freq down to 900mhz, the system only consumes about 88 watts, a 10 watt saving.

Update: don't even think about animated screensavers - running anything but "blank screen" results in the system using 121 watts continuously..

Update2:  I measured the power consumption on an IBM thinkpad with animated screensavers running and virtually no extra power was consumed - the cpu handled everything just fine without any additional stress.  Wow, guess you have to measure it...

---

### Post by tgalati4 on 2008-05-13
My Pentium D (dual-core) 2.9 GHz burns 121 watts in use and 4 watts in standby in Gutsy.  During idle it drops to around 90 watts, but there is no throttling capability in the Pentium D.  You can underclock it, but not on-the-fly.

Those P3 meters are handy.  My music/data server costs me about $67 a year running 24/7.  It's a 1 GHz celeron.

---

