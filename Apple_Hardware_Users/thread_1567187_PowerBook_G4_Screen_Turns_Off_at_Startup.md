---
title: "PowerBook G4 Screen Turns Off at Startup"
date: 2010-09-03
forum: Apple Hardware Users
---

### Post by Carleas on 2010-09-03
I recently upgraded an old PowerBook G4 that was running server 8.04.  I installed desktop and upgraded to 10.4 (I may have been able to upgrade to 10.10, I regret that I can't recall).  The upgrade went smoothly, and it worked fine for a few days. But after being off for about 36 hours, during the boot process the screen seems to be shut off.  I don't remember exactly what I was doing before this started happening, but I know I was customizing settings.  

I know I changed the login setting to automatically log in (which seems relevant because the screen shuts off just after the ubuntu loading screen), and efficiency settings (which seems relevant because the display is being shut off).

The computer doesn't shut down, and the screen isn't just blank black, it's actually off, as though it's asleep.  I have to hold down the power button to get anywhere, and it definitely turns off first.  As it happens, the words on the screen get flattened and sort of smeared around, and then the screen goes dark.

I've tried using the boot prompt, but I'm not that savvy.  When I hit tab, I see two names, 'Linux' and 'old'.  When I load 'Linux' I get the same problem.  When I load 'old' I get a bunch of error messages like these:
```
mount: mounting none on /dev failed: No such device
...
error initializing netlink socket
...
Segmentation fault
Gave up waiting for root device.  Common porblems:
-Boot args (cat /proc/cmdline)
...
ALERT! /dev/hda3 does not exist.  Dropping to a shell!
```
Then it seems to load "BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)", and goes to a "(initramfs)" prompt.

Any insights?  Is there a way to be forced to go to the login screen if I've set it to be skipped?  Or to force root login?  Can root login to the desktop?

---

### Post by Carleas on 2010-09-05
I've been able to login in single user mode by typing "Linux single" at the boot prompt during startup.  But I can't figure out what to do to make it start up normally.

During startup, right before the screen goes black, the words "sensor limit" often flash on the screen.  It's not perfectly consistent, but it makes me wonder if maybe during the normal startup the state of the laptop lid is being misread (it hibernates when the lid is closed).  How could I test this?

I can get into desktop in a low-graphics mode, I'm not sure what that means, but it seems to be the normal desktop.  I can also get droped to a command-line as root during startup, also in single user mode.  What other diagnostics can I run to test what's going wrong?

---

