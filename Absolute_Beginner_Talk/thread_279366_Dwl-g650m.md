---
title: "Dwl-g650m"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by RLR on 2006-10-17
Hello. I successfully installed this card via ndiswrapper.
I tried the driver on the CD but it did not work.
I downloaded the Win 2000 driver from D-Link website and installed it via ndis-gtk and immediately the card was detected
and all lights on card were green. I waited a couple of minutes and it detected an open wireless network and I was able to connect and surf. I also have signal strength bar in tray.
It works great so far. I will update the steps to istall ndis-gtk
and ndiswrapper for other noobs like myself.
I hope this is helpful.

---

### Post by markelhas on 2007-10-16
In my case i've managed to put it to work, but i've restart my machine and never more got a working wifi card :(. can u give me the drivers?

---

### Post by t1tough on 2008-01-12
> **markelhas said:**
> In my case i've managed to put it to work, but i've restart my machine and never more got a working wifi card :(. can u give me the drivers?

Follow [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) clause 7.3.1 and add the word ndiswrapper to the end of this file (/etc/modules) and save it. Then, restart your computer.

It works for me! :)

---

