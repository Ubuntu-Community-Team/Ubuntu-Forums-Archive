---
title: "backlight support for mbp5,5 in 11.10"
date: 2012-01-31
forum: Apple Hardware Users
---

### Post by sublime on 2012-01-31
Hello all, been a while since I've been here but I'm trying to run 11.10 on my macbook pro 5,5 and I'm having a hell of a time getting the backlight brightness keys working.  I've been working on it for a couple days now with nothing to show for it.  I've come to the conclusion that with the proprietary nvidia drivers in 11.10 the backlight module simply does not support my machine.  The pommed modules seem to not be any help as they have been sucked into the kernel and renamed apple_bl.  Adding EnableBrightnessControl=1 to the xorg.conf does nothing as well.  The only way I've been able to get the hotkeys working has been by using the nouveau video driver, but then I can't use compiz and the scale feature.

Is anyone running 11.10 on on a macbook pro 5,5 that has successfully gotten the backlight controls working?

---

### Post by alexmurray on 2012-01-31
Are you booting via EFI or BIOS emulation? If you're using EFI, the backlight is controlled via the gmux and so you'll need an updated version of apple_bl driver - see

[https://launchpad.net/~alexmurray/+archive/ppa](https://launchpad.net/~alexmurray/+archive/ppa)

---

### Post by sublime on 2012-01-31
Is there a procedure for removing the old one and adding the new one or is it simply installing the .deb?  I've installed it and no change.

---

### Post by alexmurray on 2012-02-01
Like I said, are you booting via EFI since if not then this won't help :) There is no procedure for uninstalling the old one - this replaces it - but you need to reboot once you've installed it.

Also one of the Canonical dev's is [taking this work on now]("https://lists.launchpad.net/mactel-support-community/msg00024.html") (and has incorporated the changes in the driver I originally posted above into an improved one), so [see here for more info]("https://wiki.ubuntu.com/Kernel/AppleGmuxBacklight") - I suggest you uninstall the version of the driver I pointed you to originally and use this new one instead.

---

### Post by sublime on 2012-02-01
Oops, I thought I was booting via efi but I'm not.  Grub 2 through refit.  I also find that I have no entries in /sys/class/backlight.

---

