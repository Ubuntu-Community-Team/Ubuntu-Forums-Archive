---
title: "Netgear WG311v3 Trouble"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by shopmanual on 2008-04-13
I'm trying to use ndiswrapper to get my Netgear WG311v3 working, and not getting anywhere. I installed the driver using ndiswrapper, and after I input ndiswrapper -l  it does not list anything for wlan0 . It does say that lan0 and eth0 have no wireless extensions. I've tried multiple drivers and still get the same thing. Another thing I noticed that in the tutorial when he enters ndiswrapper -l  his lists the driver as present and device with it's address as present. When I do that it only says that driver is present and **hardware** present and includes no address. Could this be the problem? And if so what should I do about it?

PS I've also tried using the -d command and it tells me that the driver is being used for that device.

---

### Post by riven0 on 2008-04-14
I don't have experience with NetGear, so I can't provide any advice. However, this wiki has apparently helped quite a few people. You may want to go through the tutorial:

[WG311v3 LINUX WIKI]("http://www.jimbo7.com/wiki/index.php?title=WG311v3_LINUX_WIKI")

---

### Post by shopmanual on 2008-04-14
At this point I'm thinking it might be my ndiswrapper, because I've done everything in that wiki, but not with the version he was using. I'm going give that version of ndiswrapper a shot, and see if it makes a difference. I'll post the results tonight and go from there.

---

### Post by shopmanual on 2008-04-15
I tried a different version of ndiswrapper, and I'm still getting the same problem. I looked through the install instructions contained in with ndiswrapper and is says that when the driver is successfully wrapped it will say driver present, hardware present, so that ends my theory that it was an ndiswrapper problem. The install seems to go smoothly, it lists something about forcing my adhoc parameters to 0, and I'm not quite sure what that means, but it doesn't seem to be a problem. Again, wlan0 is not listed and only lan0 and eth0 are listed with no wireless extensions if I input iwconfig. If I try ifconfig, there is still no wlan0 listed. What might be causing this?

---

### Post by shopmanual on 2008-04-16
Is there any way to add wlan0?

---

### Post by shopmanual on 2008-04-19
anybody?!?!

---

### Post by FoxOne on 2008-04-29
This worked for me, use the Windows98 drivers, also I used 1.52 ndiswrapper to pull this off. It can be done, if you're still having issues PM me and I'll walk you thought it. But there is tons of stuff on getting this to work in the forums. You kinda have to piece stuff together.

---

