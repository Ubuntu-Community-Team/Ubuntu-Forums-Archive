---
title: "iBook G4 Ubuntu 6.10 problems"
date: 2006-10-27
forum: Apple PPC Users
---

### Post by Termina on 2006-10-27
I just picked up a 1.07Ghz/256mb RAM iBook the other day (hey, it was only $200, how can you go wrong?).

I downloaded 6.10 for PPC, and went on the live CD. The problem is that the wireless card is not working; apparently it uses the bcm43xx wireless driver. Yuck.

dmesg | bcm43xx shows (ignoring the [numbers] before the messages):
bcm43xx driver
bcm43xx: Error: Microcode "bcm43xxmicrocode5.fw" not available or load failed.

Then it repeats that 2nd line 5 more times.

I'm not going to toss the install of Mac OS if I can't get wireless working on the live CD. Could anyone help me out? I grabbed the AirPort driver from the HFS partition (/System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2 )
but I don't know where to go from here.

Any help would be greatly appreciated. :)

---

### Post by soapboy on 2006-10-27
Follow the directions here, if you have the same chipset you will be in luck:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Got my Airport Extreme working in about 5 minutes, with no messing around with that AppleAirPort2 firmware [-(

EDIT: Fixed URL ](*,)

---

### Post by Termina on 2006-10-27
Thanks for the reply. :)

Did you post the wrong link, though? That doesn't seem to have anything to do with wireless

---

### Post by soapboy on 2006-10-27
> **Termina said:**
> Thanks for the reply. :)

Did you post the wrong link, though? That doesn't seem to have anything to do with wireless

LMAO yes I did post the wrong one. :cool: 

Here is the correct one, good luck:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

