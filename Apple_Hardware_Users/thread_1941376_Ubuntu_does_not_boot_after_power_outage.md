---
title: "Ubuntu does not boot after power outage"
date: 2012-03-15
forum: Apple Hardware Users
---

### Post by godfreypilot on 2012-03-15
I have Ubuntu installed on a macbook pro 13".  I boot via an efi boot selector followed by the standard grub bootloader.

After my computer lost power (while running Ubuntu), my computer will no longer boot into Ubuntu: after selecting Ubuntu in the Grub menu, it just loads a blank screen that says the battery state is okay and then does nothing else.

Any ideas as to what could cause Ubuntu not to boot after a power failure?

Thanks!

Ryan

---

### Post by miegiel on 2012-03-15
Corrupted files that ubuntu needs to boot. Did you try booting the recovery option in grub? Else try booting from a liveCD.

Possibly you can get things running after doing a *fsck* on the ubuntu partition. See [man fsck]("http://manpages.ubuntu.com/manpages/oneiric/man8/fsck.8.html") for more info.

---

