---
title: "Macbook pro 11,1 (2014 retina MGX) -- suspend/resume not working"
date: 2014-09-05
forum: Apple Hardware Users
---

### Post by shx2 on 2014-09-05
I installed 14.04 on my new MBP -- the new retina MGX version (July 2014).

I followed the instructions [here]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy") (which presumably were written for the older 11,1 retina version).

When I close the lid it seems to go into suspend as expected. but when I open it again, it takes a really long time to wake up (display and keyboard backlight are black).  I found that **it always takes a multiple of 10 seconds to wake up**, almost always 40 seconds.

The screen sometimes flickers once or twice just before waking up.

I also created a script in /etc/pm/power.d/ which just appends the time to a file, and it shows the same gaps (always a multiple of 10 seconds, +/- 1sec).

Here's the output of <dmesg -d>, showing the 40seconds gap (the lid was only closed for 2 seconds). Note the 40seconds gap between 83.52 and 123.53 (this is reproduceable).

[   78.638072 <   41.011315>] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[   82.003940 <    3.365868>] cfg80211: Calling CRDA to update world regulatory domain
[   82.010070 <    0.006130>] cfg80211: World regulatory domain updated:
[   82.010078 <    0.000008>] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   82.010083 <    0.000005>] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   82.010087 <    0.000004>] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   82.010090 <    0.000003>] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   82.010093 <    0.000003>] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   82.010096 <    0.000003>] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   83.352944 <    1.342848>] init: anacron main process (2526) killed by TERM signal
[   83.443056 <    0.090112>] PM: Syncing filesystems ... done.
[   83.446486 <    0.003430>] PM: Preparing system for mem sleep
[   83.446610 <    0.000124>] Freezing user space processes ... (elapsed 0.001 seconds) done.
[   83.448175 <    0.001565>] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[   83.449319 <    0.001144>] PM: Entering mem sleep
[   83.449353 <    0.000034>] Suspending console(s) (use no_console_suspend to debug)
[   83.449523 <    0.000170>] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[   83.449619 <    0.000096>] sd 0:0:0:0: [sda] Stopping disk
[   83.488490 <    0.038871>] PM: suspend of devices complete after 39.020 msecs
[   83.504375 <    0.015885>] PM: late suspend of devices complete after 15.877 msecs
[   83.520335 <    0.015960>] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
[   83.520369 <    0.000034>] PM: noirq suspend of devices complete after 15.986 msecs
[   83.520596 <    0.000227>] ACPI: Preparing to enter system sleep state S3
[   84.808819 <    1.288223>] [drm:hsw_unclaimed_reg_clear] *ERROR* Unknown unclaimed register before writing to c7204
[   84.808820 <    0.000001>] [drm:hsw_unclaimed_reg_check] *ERROR* Unclaimed write to c7204
[  123.536057 <   38.727237>] PM: Saving platform NVS memory
[  123.536206 <    0.000149>] Disabling non-boot CPUs ...
[  123.537397 <    0.001191>] kvm: disabling virtualization on CPU1
[  123.639961 <    0.102564>] smpboot: CPU 1 is now offline
[  123.641363 <    0.001402>] kvm: disabling virtualization on CPU2
[  123.743999 <    0.102636>] smpboot: CPU 2 is now offline
[  123.744325 <    0.000326>] Broke affinity for irq 58
[  123.744327 <    0.000002>] Broke affinity for irq 59
[  123.744329 <    0.000002>] Broke affinity for irq 60

I also tried 13.10, upgrading the kernel, etc. to no avail.

Any help would be appreciated.

---

### Post by este.el.paz on 2014-09-12
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)


Probably best to file a bug report about it . . . but, really it's "working" . . . it's just "slow" . . . .  I have a bug report filed for "Failure to wake from suspend in iBook 14.04 PPC" . . . in my iBook clicking "suspend" drops into a black screen, but the fan is still blowing . . . and then it doesn't "wake up" . . . at all . . . have to shut down and cold boot, etc.  

In filing my bug report I noticed that others are there for "suspend/resume" issues . . . so you might be able to piggyback on to another bugz report . . . preferably for an Apple, although since it's probably a "kernel" thing it might not matter.  I was just trying to get some bounce for PPC so I filed a new one . . . .  But Apple is still a "niche" in linux so filing a bug report will help development for apple friendly distros . . . the squeeky wheel gets the attention . . . .

e.e.p.

---

