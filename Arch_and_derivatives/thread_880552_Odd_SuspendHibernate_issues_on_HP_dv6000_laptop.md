---
title: "Odd Suspend/Hibernate issues on HP dv6000 laptop"
date: 2008-08-05
forum: Arch and derivatives
---

### Post by ladr0n on 2008-08-05
I am currently dual-booting Arch and Ubuntu on my dv6000 (AMD version, Nvidia Geforce 8400 graphics).  As this is a pretty common model, most of my hardware works flawlessly on both setups.  I am having an interesting problem with suspend and hibernate, though.
In Ubuntu 8.04, suspend worked flawlessly, and I don't remember having to do anything special to set it up.  I couldn't get hibernate to work though, regardless of what I did.  Important info: acpi suspend works in linux on this mobo.

In Arch, hibernate works (almost) perfectly with pm-utils.  Suspend works very predictably.  After I boot the laptop, I can suspend once, and it appears to work flawlessly.  If I try to suspend again before rebooting, it will hang right before putting the hardware into suspend mode.  

This behavior is the same using pm-utils and s2ram.  It does not matter whether I call a suspend from X or a vt, whether Compiz is running or not, or whether or not I am logged in (i.e. calling suspend from the GDM menu has the same result).  My /var/log/pm-suspend.log files from a successful and unsuccessful suspend are as follows:

Success:```
 Initial commandline parameters: 
Fri Aug  1 12:04:31 EDT 2008: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/01grub suspend: not applicable.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/11netcfg suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/55battery suspend: success.
/usr/lib/pm-utils/sleep.d/65alsa suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Fri Aug  1 12:04:35 EDT 2008: performing suspend
Fri Aug  1 12:04:53 EDT 2008: Awake.
Fri Aug  1 12:04:53 EDT 2008: Running hooks for resume
/usr/lib/pm-utils/sleep.d/99video resume: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume: success.
/usr/lib/pm-utils/sleep.d/95led resume: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq resume: success.
/usr/lib/pm-utils/sleep.d/90clock resume: success.
/usr/lib/pm-utils/sleep.d/65alsa resume: success.
/usr/lib/pm-utils/sleep.d/55battery resume: success.
/usr/lib/pm-utils/sleep.d/50modules resume: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume: not applicable.
/usr/lib/pm-utils/sleep.d/11netcfg resume: success.
/usr/lib/pm-utils/sleep.d/10NetworkManager resume: success.
/usr/lib/pm-utils/sleep.d/05led resume: not applicable.
/usr/lib/pm-utils/sleep.d/01grub resume: not applicable.
/usr/lib/pm-utils/sleep.d/00clear resume: VT_DISALLOCATE: Device or resource busy
deallocvt: could not deallocate console 63
Returned exit code 1.
Fri Aug  1 12:04:55 EDT 2008: Finished.

```
Failure:```
Initial commandline parameters: 
Fri Aug  1 12:11:25 EDT 2008: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/01grub suspend: not applicable.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/11netcfg suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/55battery suspend: success.
/usr/lib/pm-utils/sleep.d/65alsa suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Fri Aug  1 12:11:29 EDT 2008: performing suspend

```
As you can see, upon resuming from a successful suspend, the script fails to deallocate vt63.  I have tried manually deallocating this vt after a successful suspend, but it gives the error message:
```
% sudo deallocvt 63
VT_DISALLOCATE: Device or resource busy
deallocvt: could not deallocate console 63
```

If there are any other config files/error messages you'd like to see, just ask.
Any ideas as to how I can resolve this?

---

