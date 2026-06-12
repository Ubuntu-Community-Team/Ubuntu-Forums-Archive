---
title: "20&quot; Rev A iMac rocking with Edgy! - stock kernel"
date: 2006-10-27
forum: Apple PPC Users
---

### Post by stream303 on 2006-10-27
I can't thank you all enough!  I've got a quiet iMac running just fine with the stock kernel and 1680x1050 resolution without recompiling.

I just did a clean install of Edgy using my entire drive.  I sufferred through the noisy fans and fixed it by following this thread dealing with installing powernowd.  It is already part of the install, so I didn't have to apt-get it.

[http://ubuntuforums.org/showthread.php?t=284508](http://ubuntuforums.org/showthread.php?t=284508)

Just do sudo -s to become root temporarily and type a few lines in terminal ...so nice to hear the fans slow after hitting return!

Fixed the screen resolution from the default of 1024x768 with my nVidea card to the 20" iMac's 1680x1050 by following this thread:

[http://ubuntuforums.org/showthread.php?t=280190](http://ubuntuforums.org/showthread.php?t=280190)

In preferences I selected subpixel smoothing for the fonts, changed the mouse cursor to a larger one, and then added my HP 5650 printer without breaking a sweat.

Thanks again to all!

---

### Post by stream303 on 2006-10-28
Day two: no surprises so far.  However, I need to find a way to sleep/hibernate, and adjust screen brightness. (it's fine now but I'd like to have that control).  Threads here suggest that I might have to wait for the next kernel, but I'm just happy my G5 iMac is finally up and running with Edgy's stock kernel!

Quick recap: (thanks to the forums!)

Control the fans - 3 steps
```
1) sudo -s  (get into a root shell)
2) cd /lib/modules/$(uname -r)/kernel/drivers/macintosh
3) ls | cut -d. -f1 | xargs -n1 modprobe  (don't forget that period after -d.)
```


Make sure fans are controlled at boot:
```
lsmod | cut -d" " -f1 | grep windfarm >> /etc/modules
```

Get proper screen resolution:
```
1) lspci  (just to check to make sure what card my iMac is using)
2) sudo dpkg-reconfigure -fgnome -phigh xserver-xorg
```

This brings up a gnome dialog that lets you choose the open-source nv driver and proper resolution for 1680x1050 (20" screen)

With all that real estate I'm now playing with the large-print theme and liking it.  Added the cpu frequency scaling applet and it shows the changes when necessary between 900 and 1.8 ghz ...

---

