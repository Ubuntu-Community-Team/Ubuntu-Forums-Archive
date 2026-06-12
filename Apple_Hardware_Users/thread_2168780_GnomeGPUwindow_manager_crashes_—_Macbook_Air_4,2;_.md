---
title: "Gnome/GPU/window manager crashes — Macbook Air 4,2; Ubuntu 13.04"
date: 2013-08-19
forum: Apple Hardware Users
---

### Post by chas-d on 2013-08-19
I recently installed 13.04 on my Macbook Air 4,2, largely following the directions provided [here]("https://help.ubuntu.com/community/MacBookAir4-2") (tweaked as necessary for 13.04 and avoiding the wifi driver change).  I've generally been enjoying the system, except for ~once daily crashes of the window manager in a couple of different circumstances:


[LIST]
[*]connecting or disconnecting an external monitor while running 
[*]waking from suspend 
[*]resuming from hibernation 
[/LIST]

I'd estimate that these actions result in a crash 1/4 of the time (specifically, a flash of the normal screen, then switch to black + blinking cursor, then back at the login screen; I once had to dump to tty1 to restart X).  I've not been able to catch any useful log information so far, *until now*! :-)  See attached for a portion of the syslog that details what happened when I disconnected my external monitor; this apparently caused the system to think that the built-in LCD was also removed, which preceded a pthread segfault and some fatal gnome-session IO error.  This particular crash dumped me back at the login screen.

I've read a number of threads related to video driver issues related to macbook airs, but many/most of them are fairly out of date, and describe much more severe/frequent problems than I'm experiencing.  One apparent FAQ is this grub setting; AFAIK, mine is set as necessary (and recommended in the installation guide I followed):

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 resume=/dev/sda3"
```

In any case, any troubleshooting assistance would be greatly appreciated; I'd like to eliminate the stress associated with suspending, connecting a monitor, etc.  Let me know what further information would be helpful.

Cheers,

- Chas

[ATTACH]245472[/ATTACH]

---

### Post by chas-d on 2013-08-19
A minor note; had another X failure, this time clearly caused by a GPU hang.  It appears that I am affected by [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/946899"), though this failure was different than others (I had to force a reboot, the screen was frozen, keyboard unresponsive, and I couldn't switch to tty1).  My syslog contained these key lines, identical to those noted in the bug:

> Aug 19 14:02:55 cle-mba kernel: [36266.624209] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
Aug 19 14:02:55 cle-mba kernel: [36266.624215] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state

So, it looks like I have a bevy of GPU/window manager issues&#8230;

---

