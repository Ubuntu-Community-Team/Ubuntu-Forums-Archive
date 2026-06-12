---
title: "Ubuntu/Linux hardware compatibility sweet spot?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by LifeZagger on 2007-11-11
This might be more appropriate for the hardware forum, but I consider it a beginner question...

I'm fairly new to Ubuntu - been using it on the desktop and laptop for 1.5 weeks now.  This is the first time a linux distro has run great for me - every time I have tried to set up a distro in the past I have always had some kind of hardware issue that prevented me from going forward.

Currently all my hardware (both desktop and laptop) is 3-5 years old, and I suspect that is why everything went smoothly this time (years to build compatibility in linux).  I am intending to build a new desktop in the next 6-8 weeks, and I want to make sure that what I build will be fully functioning with Ubuntu.  I've spent some time reading the hardware forum, specifically the compatibility lists, and while those lists are helpful on a case by case basis, they aren't exhaustive.  Any other linux compatibility list I have found on the interet also seems to be limited by the amount of contributions and none are fully exhaustive.  I don't plan on building anything totally cutting edge - my main focuses are a dual core chip and making sure dual screen output works well on linux.  

Which bring me to my actual questions... ;)

Is there a sweet spot of hardware "newness" at which linux compatibility is usually available?  It seems as if it often takes the open source developers a little bit to catch up with new chipsets, video cards, etc.  

Also, can someone perhaps provide some guidance on how they built an up to date machine making sure it was fully compatible before they bought it.  I would hate to purchase hardware and have problems with linux (thereby forcing me to use XP exclusively again).

Thanks in advance!

---

### Post by shamushand on 2007-11-11
I bough this desktop less than 2 years ago, and was very lucky that everything worked with Feisty when I installed it last week. Very well then, I'll share my deep well of knowledge about Linux compatibility:
[LIST]
[*]Do NOT buy a computer with an ATI graphics card. They are very problematic with Linux.
[*]HP usually has the best computers with open-source compatible hardware.
[*]Dell sells computers with Ubuntu installed (see [here]("http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs")), so it works out of the box.
[*]64 bit is problematic with Linux.
[*] Wait about 2 months before installing the latest release of Ubuntu (e.g.: 7.10)
[/LIST]

If you insist on building your own PC, do what I did before I installed Linux - look up each piece of hardware you want in these forums. If there are a lot of thread about it, it's usually problematic, so look fora different one. Hope this helps you out! :)

---

### Post by Flying caveman on 2007-11-11
I would say an AMD64 X2 6000+ 4GB Ram and a nVidia 7600GT is fairly new and I'm not having any problems.  ASUS M/B w/ nVidia chipsets

Yes , I'm running 64bit Ubuntu 7.10, and i didn;t even have any problems getting my Broadcom 43xx wireless working,  I don't know what the problem is, :confused:

I can run XP in Virtual box (although i have no reason to) while running Folding@home and watching a DVD.

I don't think there's an answer to that question. ? Brand new hardware doesn't always work in the Windows world either.

Don't feel like you have to build an ancient computer though.

---

### Post by LifeZagger on 2007-11-12
Thanks for the responses!  I am definitely looking to build my own, so I wouldn't be going Dell or HP lets say.

I'm also thinking it is best to go with Nvidia instead of ATI based on what I have read here.  I have a ATI Radeon 7500 (card is about 5.5 years old) that has served me well, but it seems like Nvidia is a little more linux friendly.

I'm thinking something along the lines of what the Flying Caveman has system wise - I have my eye on a mobo (GIGABYTE GA-73UM-S2H), but I can't find any reference to it being used with linux (successfully or not) on the internet.  I'd really be unhappy if I couldn't run ubuntu successfully, and I'm too much of a beginner to blaze the trail on a new mobo.  

I think I'm just going to have to do more homework than I'd do for a purely Windows machine, and scour the hardware forums to make sure at least someone is having success with my intended purchase.

Thanks again for your input.

---

### Post by robinl on 2007-11-12
Usually there shouldn't be any problems with the mobo, since you don't need chipset drivers and network/sound drivers are quite good. The one thing that might be problematic would be RAID arrays, but even in that regard it's reasonably good.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
amd is comeing out with quad core cpu's that are worth waiting for not only the 4x cores but the did stuff to em and they say it should compet with intel finaly
they should be comeing in 08  and i am going to wait for em saveing my pennes

---

### Post by LowSky on 2007-11-12
> **shamushand said:**
> I bough this desktop less than 2 years ago, and was very lucky that everything worked with Feisty when I installed it last week. Very well then, I'll share my deep well of knowledge about Linux compatibility:
[LIST]
[*]Do NOT buy a computer with an ATI graphics card. They are very problematic with Linux.
[*]HP usually has the best computers with open-source compatible hardware.
[*]Dell sells computers with Ubuntu installed (see [here]("http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs")), so it works out of the box.
[*]64 bit is problematic with Linux.
[*] Wait about 2 months before installing the latest release of Ubuntu (e.g.: 7.10)
[/LIST]

If you insist on building your own PC, do what I did before I installed Linux - look up each piece of hardware you want in these forums. If there are a lot of thread about it, it's usually problematic, so look for a different one. Hope this helps you out! :)

ATI is getting better and are releasing open source drivers, just keep in mind that Linux cannot make use of DX10 so you don't need waste a ton of money on the newest cards unless you plan on duel booting with Windows Vista

64bit is just as problematic as 32 bit, don't go making up lies based on hearsay. 64bit is the future of computing and scaring people into not using it is ridiculous.

HP stuff run pretty good, except for the laser jet 1000 line, they all need to be tweaked.

dell has Ubuntu pre-installed... but who wants a dell if you know how to build a computer 

i've been running gutsy since it august and it works great

---

### Post by zetetic on 2007-11-12
I think you can get all information you are seeking on this sites:

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
[http://www.fsf.org/resources/hw/](http://www.fsf.org/resources/hw/)
[http://leenooks.com/](http://leenooks.com/)
[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)
[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)
[https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
[http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html)
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
[http://www.linuxcompatible.org/](http://www.linuxcompatible.org/)
[https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards](https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards)
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)
[http://www.tldp.org/HOWTO/Hardware-HOWTO/index.html](http://www.tldp.org/HOWTO/Hardware-HOWTO/index.html)
[http://wiki.gnewsense.org/Main/RecommendedHardware](http://wiki.gnewsense.org/Main/RecommendedHardware)
[http://www.tldp.org/HOWTO/Unix-Hardware-Buyer-HOWTO/index.html](http://www.tldp.org/HOWTO/Unix-Hardware-Buyer-HOWTO/index.html)
[http://en.tldp.org/HOWTO/Hardware-HOWTO/index.html](http://en.tldp.org/HOWTO/Hardware-HOWTO/index.html)

cheers,
zetetic

---

