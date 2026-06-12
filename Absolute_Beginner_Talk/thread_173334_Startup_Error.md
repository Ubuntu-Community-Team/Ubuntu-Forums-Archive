---
title: "Startup Error"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-05-10
ntb.ubuntulinux.org failed. What is this error that comes in the startup? Thanks!

---

### Post by Sendervictorius on 2006-05-10
Perhaps you mean ntp.ubuntulinux.org.

ntp.ubuntulinux.org is a network time server. It is an accurate time source that you pc synchronises your pc clock to on bootup -  using the network time protocol (ntp).

---

### Post by Borniet on 2006-05-10
[QUOTE=amitroy5]ntb.ubuntulinux.org failed. What is this error that comes in the startup? Thanks![/QUOTE]

[Google Search on ntp.ubuntulinux.org]("http://www.google.be/custom?hl=en&ie=ISO-8859-1&oe=ISO-8859-1&client=pub-2909160283016211&channel=2411666173&cof=FORID%3A1%3BGL%3A1%3BBGC%3A99CCFF%3BT%3A%23336699%3BLC%3A%23440066%3BVLC%3A%23d03500%3BALC%3A%23440066%3BGALT%3A%239A2C06%3BGFNT%3A%23223472%3BGIMP%3A%23223472%3BDIV%3A%2333FFFF%3BLBGC%3ACCE5F9%3BAH%3Acenter%3B&domains=bit.beheydt.be%3Bwww.beheydt.be&q=ntp.ubuntulinux.org&btnG=Search&sitesearch=&meta=")
It is ntp, not ntb, which stands for Network Time Protocol.
The error can have several reasons, but the main thing is that for some reason your Ubuntu cannot reach the Time Server.

You can either disable this by:

'sudo rm /etc/rcS.d/S51nptdate'

or you can change the default behavior by editing /etc/defaults/ntpdate, commenting NTPSERVERS="ntp.ubuntulinux.org" out and uncommenting NTPSERVERS="pool.ntp.org"

---

