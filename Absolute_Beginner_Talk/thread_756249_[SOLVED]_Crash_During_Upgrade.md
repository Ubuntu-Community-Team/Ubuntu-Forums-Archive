---
title: "[SOLVED] Crash During Upgrade"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by ssdurn on 2008-04-15
Hi

My machine crashed during a upgrade.

I can now login but then just get a blank screen (not the wallpaper) and mouse pointer and nothing else.

I can start the recovery console but don't quite know what to do when I'm there.

Any help is as always appreciated.

---

### Post by Tatty on 2008-04-15
is this a distro upgrade or just a typical maintenance upgrade?

First i would back up everything you cant afford to lose just in case

its probably worth trying to continue the update to see what happens:
```

sudo apt-get update
sudo apt-get upgrade
```

if it still fails to load a GUI then try reconfiguring xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

---

