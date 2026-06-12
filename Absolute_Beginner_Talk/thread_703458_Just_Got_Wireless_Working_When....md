---
title: "Just Got Wireless Working When..."
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by darKStorm on 2008-02-21
...I rebooted the system, and on Network (System -> Administration -> Network) the option for wireless configuration had gone, why is this, how do I get it back, and how do I make it permanent?

---

### Post by zerhacke on 2008-02-21
sudo insmod ndiswrapper I would bet would return wlan0.  Or was it sudo modprobe ndiswrapper?  I can't remember which right now.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

### Post by darKStorm on 2008-02-21
The first one brings an error message which says "insmod: can't read 'ndiswrapper': No such file or directory", the latter doesnt do anything, but still doesnt bring up the Wireless connection setting, do you know of anything else that could work?

---

