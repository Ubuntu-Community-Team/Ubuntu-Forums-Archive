---
title: "ASUS K42Jr overheat and fan noise with Ubuntu 11.10"
date: 2012-03-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dreamgazer on 2012-03-01
My ASUS K42Jr produce overheat and fan noise everytime i boot into ubuntu 11.10. I'm using dual boot here.
This is the first time i'm using ubuntu on laptop and on dual boot with windows.

My questions:
1. Does this happens to every laptop or every dual bool install?
2. Is there any solution to this problem?

I've been a casual user of ubuntu since 2008. Don't know much about command line and stuff. Please be easy on me... :)

---

### Post by xycris on 2012-11-09
i have the same issue with overheating with my unit.

i have an asus k53sv with intel core i5, 8gb ram, intel hd graphics 3000 and nvidia geforce gt540m with 2gb memory and 750 gb hdd.

with windows (the supplied os), it does not heat up that much with just regular internet browsing and the fan noise cannot be noticed. but with ubuntu 12.04 and now i have 12.10, heating up is an issue and my unit just suddenly reboots and all my documents are lost if not saved or autorecovered by libreoffice.

i have psensors running. i have this typical scenario: psensor reports to me temps of at least 56 degrees C for 5 sensors (the hdd is at 49 degrees C) at startup. when one of the sensors reports 60 degrees the fans just turns leading to a noticeable noise. this is typical when opening twitter and facebook in firefox. when i play a video either in youtube or facebook, the fan just flares up its rpm and noise is more audible.

open libreoffice while playing youtube vid then there is a possibility that the unit just shuts off and do a reboot.

because of this i seldom use ubuntu. i have another linux distro up and it is Mandriva (KDE) in an external hd via usb3. my unit heats up too but only during rendering of movies in kdenlive or running data in r (via rkward).

by the way, i also have CPU Frequency Scaling Monitor installed but it seems to me that it has no effect.

typical cpu usage is at 10% all the way with just regular browsing despite the heating.

how can we keep our units cooler?

thanks in advance for your help.

---

### Post by 2F4U on 2012-11-09
> 1. Does this happens to every laptop or every dual bool install?

No, many laptops out there are running cool under Linux. There are couple of possible reason if they don't. In your case, since the burden on the CPU seems low, I would guess that the reason is the hybrid graphics.

[http://www.phoronix.com/scan.php?page=news_item&px=MTIxOTM](http://www.phoronix.com/scan.php?page=news_item&px=MTIxOTM)
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

