---
title: "Undoing an Install of Softmac."
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by AlphaMack on 2006-03-23
I somehow screwed up following all of the instructions on this page...
[http://www.fisica.unipa.it/~lavaget/ubuntuae/](http://www.fisica.unipa.it/~lavaget/ubuntuae/)

At this point I just want to get rid of everything Softmac dropped into my system and installing bcm43xx and start clean again.  Where do I even begin to figure out how to undo all of the sym links and whatever else was dumped onto my system?

I tried to go back to installing fwcutter/bcm43xx as outlined in this thread...
[http://www.ubuntuforums.org/showthread.php?t=142727&highlight=Airport+Extreme](http://www.ubuntuforums.org/showthread.php?t=142727&highlight=Airport+Extreme)

And now I get this when I modprobe bcm43xx...

[b]WARNING: Could not open '/lib/modules/2.6.15-19-powerpc/kernel/net/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-19-powerpc/kernel/net/ieee80211/ieee80211.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-19-powerpc/kernel/net/ieee80211/softmac/ieee80211softmac.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.15-19-powerpc/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko': No such file or directory
[/b]

Going to dmesg, I get a bunch of "unknown symbol" errors.

I'm lost. :(

---

