---
title: "twinview, nVidia heads up ..."
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-07
When I turned my PC on this morning, Ubuntu booted up in single-monitor mode instead of dual-monitor "twinview" mode.  After checking the configuration, reinstalling the nVidia drivers, etc, my desktop would only show on one monitor and the other monitor I got a no signal.  It was interesting that during the boot up sequence, both monitors show normal information until the gnome login.  No matter what I did, my desktop would work only on one monitor.

So, after exhausting everything I could think of and double checking my xorg.conf file, I suspected my nVidia 6250 video card was bad.  So, remembering that I had an older instance of  Ubuntu on my hard drive, I restarted in that copy of Ubuntu -- and that one too would only work with one monitor.  Now, knowing it was not my configuration, I shut down the PC and removed the power cord for a few minutes -- then booted Ubuntu -- viola, I had twinview again!!!

So, the tip I giving you is if twinview does not seem to work and you can't figure out why, turn off power for a few minutes and then retry.  Hard Reset and Restart did not clear this for me.  Evidentually, some nVidia cards can get in a hung up state in which a complete power down is needed -- and this might be because many motherboards continue to have power on it even when you turn the PC off -- and that power might still be on the video card slots.

Carl

---

