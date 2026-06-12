---
title: "&quot;Lock screen&quot; inconsistency on suspend/resume"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by sarah_f on 2006-10-08
I'm running Ubuntu 6.06.1 and am unable to find another thread that discusses this issue.

My gconf settings are as follows:
  /apps/gnome-power-manager/lock_use_screensaver_settings = false
  /apps/gnome-power-manager/lock_on_suspend = true

In screensaver preferences:
  Set session as idle after = 10 minutes
  Lock screen when screensaver is active = false

In power management preferences:
  Put display to sleep when computer is inactive for = 30 minutes
  Put computer to sleep when it is inactive for = 1 hour
  Sleep type when inactive = Suspend

If I select "suspend" from the "System/Quit" menu, my computer requires a password when I resume (which is my desired operation).  However, if my computer suspends due to exceeding the inactivity setting, then it DOES NOT require a password when I resume.

Why doesn't the "inactivity" suspend function exactly like a "manually requested from the menu" suspend?  How can I make them both require a password upon resume (without forcing the screensaver to require one)?

Thanks for any info provided.

---

### Post by mdsmedia on 2006-10-10
If for no other reason than to bump this message, for what it's worth, I get the same inconsistency with Suspend/Lock when I close my notebook's cover. At first it locked every time. Now it will sometimes lock and sometimes it won't. More often it won't. The last couple of times it did.

I'd love to know how I can fix this and why it is inconsistent.

---

