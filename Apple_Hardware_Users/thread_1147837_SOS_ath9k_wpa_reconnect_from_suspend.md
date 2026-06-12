---
title: "SOS ath9k wpa reconnect from suspend"
date: 2009-05-03
forum: Apple Hardware Users
---

### Post by Rog-Mahal on 2009-05-03
I posted [here in the Networking and Wireless section]("http://ubuntuforums.org/showthread.php?t=1147575") of the forums regarding this issue, but I figured I would try the Apple forum too. I'm running Jaunty 64 bit on a MacBook 2,1.

My wireless connects with no problems on a cold boot or a reboot, but when resuming from suspend two things happen:

With network-manager:

I get asked repeatedly for my network password, but it never connects and ends up giving up.

With wicd:

If I use wext as the wpa supplicant, connection stalls at "Receiving authorization". If I use the ralink legacy, it stalls at "Obtaining IP address". 

The post in the link contains the (I think) relevant dmesg output. I've checked bugzilla and launchpad about the error, and the following fixes have not worked:

Installing wicd.
Installing the jaunty-backports package
Modprobing ath9k
Modprobing ath_pci

I had wireless working well in 8.10 with a WPA2 network, and it worked fine with 9.04, but I had to switch to WPA because OS X wouldn't connect to the WPA2 network.

Any help would be greatly appreciated!

---

### Post by cyberdork33 on 2009-05-03
you want wext.

you should only use ath_pci if you are NOT using ath9k and vice versa. ath_pci is part of madwifi and should be blocked if you are using ath9k.

You could also resort to ndiswrapper...

---

### Post by Rog-Mahal on 2009-05-03
well, I love having completely open source drivers... After removing wicd and reinstalling nm and rebooting I've been able to connect successfully after modprobing ath9k. And I don't have ath_pci (probably why it didn't help the problem). Maybe it was just being squirrelly.

---

