---
title: "Mint wifi?"
date: 2012-01-27
forum: Any Other OS
---

### Post by /bin/sh on 2012-01-27
I have linux mint 10 64-bit and once I rebooted and the wifi did not work, so I checked in additional drivers and the broadcon STA wireless driver was not activated so I activated but then it gave me this error message:

Sorry, the installation of this driver failed.

Please have a look at the log file for details.: /var/log/jockey.log

I looked in there and it said this:

2012-01-27 21:28:15,704 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-01-27 21:28:15,761 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-27 21:37:02,103 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-27 21:37:02,335 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-27 21:37:02,419 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-27 21:37:05,164 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-27 21:37:07,147 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-27 21:37:07,165 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-01-27 21:37:07,281 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-27 21:37:18,003 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-27 21:37:18,036 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-27 21:37:18,087 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-27 21:37:21,721 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-27 21:37:22,566 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-27 21:37:22,571 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-01-27 21:37:22,610 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

Please help as I urgently NEED wifi.
PS: I have a cable internet connection if I ned to install anything.

---

### Post by oldos2er on 2012-01-27
Moved to Other OS/Distro Talk.

---

