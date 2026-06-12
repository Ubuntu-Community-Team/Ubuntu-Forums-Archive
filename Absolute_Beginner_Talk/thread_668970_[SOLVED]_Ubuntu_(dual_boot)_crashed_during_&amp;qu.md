---
title: "[SOLVED] Ubuntu (dual boot) crashed during &amp;quot;screen lock&amp;quot; now it won't boot :("
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-16
I ran into a weird problem today, unforunately I can't seem to be able to pause the load screen long enough to get the error message so I'll relay what happened that seemed to lead up to my problem.

I'm running a dual-boot with Ubuntu and XPx64 on a single drive with XP having been installed first.  Everything seemed good.  I stepped away from my computer for a few hours today and before doing so I locked the screen.  As far as I can remember I turned off the screen saver and disabled the powersave settings.

When I tried to log back on (the screen was black) all I got in response was the mouse cursor, which responded to movement, but that was all.  I did a hard reboot on the system and the first thing I noticed was the drive my OSes were installed on wasn't recognized.  I shut the power off, disconnected the power cable to the IDE drive, reconnected, and powered it on.  Everything looked good.  GRUB came up and it began to boot into Ubuntu.

Before the splash screen hit a brief message came up, it went by so fast I was unable to catch it but I recall it didn't look good.  Possibly something about something being disconnected or uninitialized, I really can't say.  The splash screen with the Ubuntu progress bar came up, it got about 2% done then it hangs and my CAPS lock begins blinking on my keyboard.  To get the CAPS lock to stop I have to power off the system and disconnect the PS2 keyboard cable.

This happens *every* time I try to load up Ubuntu.  XP on the other hand, loads up without a hitch.

With Linux I haven't a clue where to go.  From my experience with Windows my first point of blame would be to try the video drivers.  I'm using an ATI 9600 Pro and have yet to load or find the drivers to load into Ubuntu.  Though I've no idea if that will help or if it's related.

I'm just wondering if anyone has any thoughts.  Right now my next step will probably be to reload Ubuntu.

Thank in advance :)

---

### Post by dgray_from_dc on 2008-01-16
From what you described, your problem probably isn't your video driver.  It sounds far more serious than that.  Can you get it to boot into single user mode?

---

### Post by jken146 on 2008-01-16
Try booting into Recovery Mode (aka single user mode).  You should be able to see any error messages you get there.

To reconfigure your X server, run this command in Recovery Mode:
```
dpkg-reconfigure xserver-xorg
```

---

### Post by toastysquirrel on 2008-01-19
Thanks guys.  Given the numerous other install/performance/stability issues I've had since trying to install Ubuntu, I'm pretty sure it was a drive problem.  Though I'm still not sure why the drive and partition seem to be performing flawlessly with XP (which is installed on the first partition on the same disk).

---

