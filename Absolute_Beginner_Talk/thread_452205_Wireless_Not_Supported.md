---
title: "Wireless Not Supported?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-05-23
I've been checking out **Ubuntu 7.04**
on a **Dell Inspiron 1501**.

The **Dell Wireless 1390 WLAN Mini-PCI Card**
Does not seem to be working.

I've heard there has been support problems for wireless.
Is there a way I can fix it?

Thank you

---

### Post by Famicommie on 2007-05-23
If you can get it connected to the internet via ethernet, or have the necessary repository CD, then simply open up a terminal and enter the command
```
sudo aptitude install bcm43xx-fwcutter
```
That will install the proper driver for your card.

---

### Post by orb9220 on 2007-05-23
A search on google with > ubuntu Dell Wireless 1390 WLAN
gives first hit to **[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)**

Hope this helps.

---

