---
title: "CRC error when upgrading kernel version"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Kr!ztov on 2007-07-14
It sounds strange, but when I use 2.6.20-15-Generic, it works fine, like  charm, however, when I update to 2.6.20-16-Generic, I get "CRC Error - System Halted" on startup. I figure this must be something to do with the kernel, because when I go back to 2.6.20-15-Generic, it works again. Has anybody encountered this problem? Is there a solution?

System Specs:

3.2 Ghz Dual Core Pentium D
Gigabyte 945GZM-S2 (rev 3.0) Motherboard
2 Gb of DDR2 Ram, operating at 533 mhz
Onboard Gfx
USB Wireless mouse
USB Wired Keyboard, PS/2 adaptor.

Net connection:
8 Mbps
Shaped at 1024 Mb

---

### Post by apoth on 2007-07-14
A CRC check, you may know, is like an MD5 check - it checks that a file is there, complete and not corrupt. If that's throwing an error then maybe the download of the kernel didn't work quite right.

Either stick with the old kernel until a new one comes out and succeeds the corrupt kernel, or perhaps try uninstalling the corrupt kernel and reinstalling it?

---

### Post by Kr!ztov on 2007-07-14
Hmm.... It could be a bad download. I had timeout problems with upgrades earlier today, but just redownloaded the failed upgrades. Although, there could always have been a false positive. I might just wait for the new kernel. Although, is there any actual advantage using 2.6.20-16-Generic over 2.6.20-15-Generic?

---

### Post by apoth on 2007-07-14
There's a whole load of stuff in the changelog, it's in /usr/share/doc/linux-image-2.6.20-16-generic/changelog.Debian.gz. I haven't noticed a thing though!

---

