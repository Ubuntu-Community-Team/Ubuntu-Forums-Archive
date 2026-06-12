---
title: "wireless for Ubuntu"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2007-06-11
Ahhg i sense a nightmare , what type of wireless card should i get to ease the stress on myself(for computer not laptop)

I want a really good one, that i can add maybe an antenna too improve my connection(some people get good connection, depends what area of the residence you are in)

---

### Post by tdrusk on 2007-06-12
> **Brendan Hart said:**
> Ahhg i sense a nightmare , what type of wireless card should i get to ease the stress on myself(for computer not laptop)

I want a really good one, that i can add maybe an antenna too improve my connection(some people get good connection, depends what area of the residence you are in)

Look into broadcom 43xx cards. There is a package that can automatically install them.

The bcm4303, 4306, and 43xg all are fully supported..

Take a look at [this]("http://bcm43xx.berlios.de/?go=devices").

---

### Post by supazio on 2007-06-12
> **fuzzyhair said:**
> Look into broadcom 43xx cards. There is a package that can automatically install them.

The bcm4303, 4306, and 43xg all are fully supported..

Take a look at [this]("http://bcm43xx.berlios.de/?go=devices").But DO NOT get the bcm4318 unless you want a complete compatibility nightmare. Not even ndiswrapper could sort mine out, and I went through 3 fresh installs before it would finally work. Seriously. (It's the LinkSys WMP54GS)

---

### Post by Bachstelze on 2007-06-12
Avoid Broadcom :(


Buy Ralink :)

[http://www.openbsd.org/cgi-bin/man.cgi?query=ural](http://www.openbsd.org/cgi-bin/man.cgi?query=ural)
[http://www.openbsd.org/cgi-bin/man.cgi?query=rum](http://www.openbsd.org/cgi-bin/man.cgi?query=rum)

(There's a list of devices at the end. Yes, I know it's for OBSD but those will work just fine on Linux, too - and kudos to Damien for the great drivers, by the way :D )

---

### Post by malathia on 2007-06-12
> **supazio said:**
> But DO NOT get the bcm4318 unless you want a complete compatibility nightmare. Not even ndiswrapper could sort mine out, and I went through 3 fresh installs before it would finally work. Seriously. (It's the LinkSys WMP54GS)

Odd, I didn't have much problem with that chipset, once I found the appropriate way to do it. I didn't use ndiswrapper, I used the broadcom fw-clipper, can't recall name at the moment, that removes the vital driver specs from the proprietary driver and loads them directly into your lib. This doesn't give you the full 54Mbits speed, but apparently results in a cap of about 11Mbits

This is a really easy method for installing broadcom cards, to circumvent the frustration until you get NDISwrapper installed suitably (if you want full speed).

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear") worked for me on Dapper. and from reading some of the forums, it apparently has worked for others using Feisty Fawn

(KevDog from this post [http://ubuntuforums.org/showthread.php?t=465160&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=465160&highlight=broadcom") seems to have had success in Feisty)

---

### Post by Big Bear on 2007-06-12
My Intel 2200BG wireless(built-in on my laptop) was auto installed and works great... though I have no way of turning on/off the wireless that I can find except to log into my windows partition and do it from there which carries over a reboot well enough.

---

### Post by tdrusk on 2007-06-12
> **supazio said:**
> But DO NOT get the bcm4318 unless you want a complete compatibility nightmare. Not even ndiswrapper could sort mine out, and I went through 3 fresh installs before it would finally work. Seriously. (It's the LinkSys WMP54GS)

Are you referring the the broadcom bcm4318 [Airforce 54g]?
I had no problem setting up ndiswrapper with that. the bcm43xx-fwcutter package made my machine stall. I checked their site and it is not fully supported yet by bcm43xx-fwcutter. Ndiswrapper would probably be the better choice if you are experiencing performance issues.

---

