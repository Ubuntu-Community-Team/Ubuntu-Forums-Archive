---
title: "Screen resolution dropped to 640x480 (5.10 BB)"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by cls1chuck on 2006-05-03
Not sure what I did, but my screen res dropped to 640x480 between the time logged out and logged back in!  In between, I added the universe to the Breezy security updates repository.  I noticed it triggered some updates.  
History in SynPkgMgr shows:
===
Updates:
gdm (2.8.0.5-0ubuntu1) to 2.8.0.5-0ubuntu1.1
libtiff4 (3.7.3-1ubuntu1) to 3.7.3-1ubuntu1.1

Installed:
libruby (1.8.2-1)
libruby1.8 (1.8.2-9ubuntu1.1)
ruby (1.8.2-1)
ruby1.8 (1.8.2-9ubuntu1.1)

Removed:
celestia-gnome
planetpenguin-racer
scorched3d
xqf
===
The 'screen resolution' (under system/preferences) only has 640x480 as an option (same w 60Hz).
Any help is appreciated.  5.10 Breezy Badger, Trident CyberBladeXP.  Has been working great until just now.

---

### Post by Haegin on 2006-05-04
I would reccommend trying a
```

sudo dpkg-reconfigure xserver-xorg

```
from a terminal then follow it through. The defaults are normally fine and choose medium when you get asked (later on) and set the res there.

---

### Post by cls1chuck on 2006-05-05
Thanks!  Actually, I went and 'backed out' the the flashplayer-nonfree, then rebooted, and the problem was fixed.  Not sure if the fix was the reboot (I hope not!), or the uninstall, or something else.  I don't want rebooting to be a probelm solver in Linux - that's one of the many reasons I left Windows!

---

