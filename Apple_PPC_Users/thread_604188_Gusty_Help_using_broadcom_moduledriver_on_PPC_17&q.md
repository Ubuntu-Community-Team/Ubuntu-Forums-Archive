---
title: "Gusty: Help using broadcom module/driver on PPC 17&quot; G4 powerbook"
date: 2007-11-05
forum: Apple PPC Users
---

### Post by vts1 on 2007-11-05
I have spent the weekend installing a fresh gusty and it looks great esp
with compiz however I had some serious rebooting/networking issues found
to be related to the broadcom module.

I have a PPC Powerbook 17" G4 with broadcom 4306 rev 3 airport.  This as
worked just fine in Feisty but I can not for the life of me get it to
work in Gusty.  I have read much but every suggestion I found never
helped. 

What I have done:

1.  activated bcm43xx using restrictive drivers downloading the firmware from the interent.
2.  used network manager both from Feisty and Gusty but each made no difference.
3.  removed bcm43xx using restrictive drivers and still nothing.
4.  I tried to use ndiswrapper but can only install ndiswrapper-common in gusty
5.  Tried to use Debian Lenny's version of network manager as well but that just made things a bit worse.
6.  I was able to connect to a wireless network configuring it manually.

I am guessing I will not be able to use network manager in Gusty?  This does make me rather sad because I use the computer applet on my panel all the time in my accounts and it is fully depended on network manager.

After spending many hrs of researching and trying this on my own I am
seeking some help from the community.  Are there others who are still
using ppc G4 who  can help?   I would really love to use Gusty.

Thanks,
Adam

---

### Post by kugn on 2007-11-07
I've never quite had problems with bcm43xx on my iBook G4. If I read you correctly, you had 
sudo apt-get install bcm43xx-fwcutter

which includes a script to download and install the firmware. they install to /lib/firmware.

After doing that I would
sudo modprobe bcm43xx

then check that wireless works by running
iwlist eth1 scan
(eth1 is my wireless interface, which might be different from yours. you can check it with iwconfig)

well then my network manager would show the available wireless networks. 


I don't really know what you mean by removing bcm43xx with restricted drivers.

ndiswrapper only works on x86 machines. they don't work on powerpc.

hope this helps

---

