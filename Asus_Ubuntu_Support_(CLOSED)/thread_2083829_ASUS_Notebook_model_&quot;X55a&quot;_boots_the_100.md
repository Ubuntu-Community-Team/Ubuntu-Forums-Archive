---
title: "ASUS Notebook model &quot;X55a&quot; boots the 10:04 live USB (NO WI-FI Connect)"
date: 2012-11-13
forum: Asus Ubuntu Support (CLOSED)
---

### Post by inteldesign258 on 2012-11-13
I bought a new ASUS laptop! My old laptop was a HP laptop w/ standard AMD 64 architecture. The 10.04 liveUSB boots with the new ASUS, but doesn't allow the software to connect to the internet using wireless connect.
The processor in the ASUS

                                     Processor
                               Intel® Pentium® Dual-Core Processor
Intel® Celeron®             Dual-Core Processor
                 
                                     Chipset
                               Intel® Chief River Chipset HM70
                
Should I be using the i386.iso liveDVD ubuntu software instead, or can my current liveUSB be HACKED to solve my wi-fi connect issue?

Thanks,

M J

---

### Post by sigmatht on 2012-11-17
I suspect that's because your kernel doesn't have rt5390 support in it.  If you wish to still use ubuntu 10.04..  I'd recommend you create a custom Live CD.  Ubuntu has a help page on how to go about doing this.  

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by inteldesign258 on 2012-11-18
Thanks for the link...Hopefully the advice given will work!

---

### Post by inteldesign258 on 2012-11-19
[sigmatht]("http://ubuntuforums.org/member.php?u=1736888") The customization website that you directed me to is pretty comprehensive. Perhaps you or some else can help me here. The reason I cannot log-onto the internet may not be a kernel issue! It may only need a new script or patch that can be inserted ...this is just an example /usr/share/netmanager. If anbody has any suggestions I am willing to listen. the 10.04.3 LTS  liveusb must have some type of file that can be modified.

Thanks

---

### Post by sigmatht on 2012-11-20
Its a driver issue.  The reason I suggest customizing the livecd with an updated kernel is 1) the newer kernels have the driver for rt5390 built into it, and 2) that link specifically mentioned (i believe) how to customize the kernel.

You can manually install the driver from ralink--but I wouldn't have any idea on how to set that up with the customized livecd.  

Post #24 has directions on how to manually install the drivers:
[http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=3](http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=3)

But again, I don't know how you would go about adding this to the livecd... but you can certainly test installing the driver's on the livecd and see if that fixes your problems...but of course, any changes made while running a livecd aren't saved...so you'd either have to 1) customize your livecd with the driver patch or 2) go through the process of installing the driver everytime you boot via livecd.



If it was me, I'd go with the newer kernel.

Another thread might be helpful: 
[http://askubuntu.com/questions/94156/installing-with-a-different-kernel](http://askubuntu.com/questions/94156/installing-with-a-different-kernel)

---

### Post by inteldesign258 on 2012-11-21
I have looked into the matter and you happen to be right on one key point! The kernel that I currently have has to be updated, and I also found out that a special patch labeled "mac80211" has to also be installed as well. Although I still am working on solving this issue I found this following post interesting and it confirms what you have pointed out to me!

[http://forums.debian.net/viewtopic.php?f=5&t=85176](http://forums.debian.net/viewtopic.php?f=5&t=85176)

Thanks

---

