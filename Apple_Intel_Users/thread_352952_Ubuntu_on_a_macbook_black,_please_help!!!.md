---
title: "Ubuntu on a macbook black, please help!!!"
date: 2007-02-04
forum: Apple Intel Users
---

### Post by xandergt on 2007-02-04
Hi guys, i'm planing to get my first mac and i would like to know if ubuntu woks as good as on a pc, (wireless, audio, video, beryl...) i really need your help on this. 
the machine has a 2.0GHz Intel Core 2 Duo processor, 120GB 5400-rpm Serial ATA hard disk drive, 2GB Sdram, Built-in 54-Mbps AirPort Extreme Wi-Fi (802.11g), a Intel GMA 950 graphics processor with 64MB of DDR2 SDRAM shared with main memory, 6x SuperDrive (DVD+R DL/DVD±RW/CD-RW) and 13.3-inch (diagonal) glossy TFT widescreen display, 1280 by 800 resolution. beautiful isn't it .

Thanks for your comments and help.

---

### Post by maggot_brain on 2007-02-04
It's a bit of a faff on as Intel based Macs use something called EFI ([http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)) and not the old PC BIOS.  This link should be helpful:

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

I'm not sure but I think your hardware should all be supported.  The only problem being the Airport Extreme card which again is a bit of a faff on.  You'll need the X86 or AMD64, not the PPC version of Ubuntu.  Core 2 duo is one of Intel's implementations of AMD's X86-64 architecture.  If you're getting a laptop specifically or mainly to run Ubuntu I wouldn't bother with Apple hardware.  You can get similarly or better equipped laptops much cheaper with non-Apple hardware.  The only reason in my opinion to get Apple hardware is to run Mac OS X.  Others may disagree but I'm not overly impressed with OS X.  Apple only allows OS X to be installed or run on their hardware.  You can install OS X on non-Apple hardware but this involves using third party patches of dubious legality.

Ubuntu should run as well on the laptop you specified as any other Core 2 duo based system.  You could try posting a message on the X86 and AMD64 forums and see what the users there think.  I did run Ubuntu on an X86 desktop (till it broke) up until very recently and it was class!

I hope this is of some help!

Ananda

---

### Post by pauljwells on 2007-02-04
Ohhhhh!! maggot_brain!! Are you feeding the trolls??

This guy is obviously looking at a macbook, which is extremely well supported by Ubuntu, and can easily be set to triple boot Mac OSX, Windows XP and Ubuntu. Add onto this VMWare under Ubuntu or XP, Parallels in OSX (with its stunning 'coherence' mode, which lets you run XP apps as 'almost' native OSX apps) and you have the most versatile machine on the market.

Also it's **NOT** expensive for a core 2 duo machine by any means. Factor in that its resale value will be twice that of a Dell of the same cost and age, and that all Apple hardware is gorgeous, and you can't go wrong.

Get your order in today, xandergt! - You might even like OSX, it's far less flexible than linux, but it does show just how well integrated an OS really can be with its hardware.

---

### Post by maggot_brain on 2007-02-04
No I'm not feeding the trolls!  Just giving my honest opinion,

> **pauljwells said:**
> Ohhhhh!! maggot_brain!! Are you feeding the trolls??

This guy is obviously looking at a macbook, which is extremely well supported by Ubuntu, and can easily be set to triple boot Mac OSX, Windows XP and Ubuntu. Add onto this VMWare under Ubuntu or XP, Parallels in OSX (with its stunning 'coherence' mode, which lets you run XP apps as 'almost' native OSX apps) and you have the most versatile machine on the market.

Also it's **NOT** expensive for a core 2 duo machine by any means. Factor in that its resale value will be twice that of a Dell of the same cost and age, and that all Apple hardware is gorgeous, and you can't go wrong.

Get your order in today, xandergt! - You might even like OSX, it's far less flexible than linux, but it does show just how well integrated an OS really can be with its hardware.

---

### Post by grazie on 2007-02-04
Mac Intel Core Duo queries are becoming very common. Although the machines have much more in common with x86 than PPC Macs, I do think it's time for a new 'Apple Intel Core Duo Users' forum, even though the platform is not officially supported yet. How do we make it happen?

---

### Post by xandergt on 2007-02-04
Thanks a lot guys, i'll get it order now.

---

### Post by pauljwells on 2007-02-04
> **grazie said:**
> Mac Intel Core Duo queries are becoming very common. Although the machines have much more in common with x86 than PPC Macs, I do think it's time for a new 'Apple Intel Core Duo Users' forum, even though the platform is not officially supported yet. How do we make it happen?

Add your voice...

[http://www.ubuntuforums.org/showthread.php?t=353026](http://www.ubuntuforums.org/showthread.php?t=353026)

---

### Post by mustang on 2007-02-04
> **pauljwells said:**
> Ohhhhh!! maggot_brain!! Are you feeding the trolls??

This guy is obviously looking at a macbook, which is extremely well supported by Ubuntu, and can easily be set to triple boot Mac OSX, Windows XP and Ubuntu. Add onto this VMWare under Ubuntu or XP, Parallels in OSX (with its stunning 'coherence' mode, which lets you run XP apps as 'almost' native OSX apps) and you have the most versatile machine on the market.

Also it's **NOT** expensive for a core 2 duo machine by any means. Factor in that its resale value will be twice that of a Dell of the same cost and age, and that all Apple hardware is gorgeous, and you can't go wrong.

Get your order in today, xandergt! - You might even like OSX, it's far less flexible than linux, but it does show just how well integrated an OS really can be with its hardware.

"Extremely well supported by Ubuntu..." is a bit of an overstatement. Suspend and power management still do not fully work. I'd imagine those are pretty big features for laptop users. I certainly think so.

Dollar per dollar, the macbook *is* more expensive than other laptops. While I agree that their resale value is higher, not everyone is in a position to sell their laptop after they move on to a new one. I got a deal on my macbook (~730) first generation which is why I bought one (in addition to the ability to run OSX and the handsome build quality apple products have).

To the answer the OP: video, audio, beryl will work. You will need ndiswrapper for wireless. But like I mentioned, power management and suspend are still not there yet. If you need those features, I would wait until Feisty comes out.

---

### Post by xandergt on 2007-02-04
Ok. thanks mustang, and i thank you all for your help.

---

### Post by goucho29 on 2007-02-05
"This guy is obviously looking at a macbook, which is extremely well supported by Ubuntu"

you wont have much drive space left if you install Mac OSX, Windows, and Ubuntu, thats for sure. 

But touching on this, has anyone got the Ubuntu Edgy Eft (Jan 2007 distro) to install on an external FW drive (where we MacBook users tend to have lots more space) ??

Im able to boot my Intel MBP with the above distro, but can never get past the part where you have to manually assign partition tables (as I already have 3 ready to install-on partitions)

The GUI describes one needing to assign a the / to a partition and the swap space to a partition. I tried every conceivable combo and the "NEXT" button never lit up ! 

PHOOEY. So what gives ? Can this be done ? Would be cool ! Im hoping somebody out there has done it and will chime in here

---

### Post by maxamillion on 2007-02-05
With all due respect, why is this in the Apple PPC users Category?

---

### Post by Gen2ly on 2007-02-16
its NOT :)

---

