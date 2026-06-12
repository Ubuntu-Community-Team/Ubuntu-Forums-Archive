---
title: "Cannot suspend mbp 4,1 in karmic"
date: 2010-01-19
forum: Apple Hardware Users
---

### Post by jlogday on 2010-01-19
I recently upgraded a macbook pro 4,1 from jaunty to karmic.  Since the upgrade, whenever I try to suspend the laptop, I get a black screen with a blinking cursor in the upper left corner.  The only way to recover from this is to forcefully power down the laptop by holding in the power button and then reboot.

After rebooting, there are no errors in the pm-suspend log file, and no oopses or other errors that I can find.  I can get the suspend to work if I boot into the old kernel (2.6.28-17-generic), but with that kernel neither sound nor the trackpad will work.

The [guide]("https://help.ubuntu.com/community/MacBookPro4-1/Karmic") claims that suspend and resume work out of the box, which implies to me that the upgrade doesn't work properly, but a clean install does.  Can anyone confirm this?

I have also tried compiling several custom kernels, to no avail.  Older kernels (2.6.30-1) cannot suspend and do not have working sound or trackpad, while newer kernels (2.6.31-18.55) have working sound and trackpad but cannot suspend.

Does anybody have any suggestions how to proceed from here?  Here are the last few lines of /var/log/pm-suspend.log, in case it helps:

```
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Mon Jan 18 17:06:08 EST 2010: performing suspend
```

---

### Post by jlogday on 2010-01-20
Is **anybody** using karmic on a macbook pro 4,1?

---

### Post by jlogday on 2010-01-25
I "solved" this by reformatting and reinstalling karmic.  Like the guide says, suspend works out of the box (on a clean install).  Resume, however, does not -- I had to enable the restricted nvidia driver before resume would work.  Since I was planning to do this anyway, that's not really a big deal, but it deserves mentioning.

---

