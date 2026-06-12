---
title: "Ubuntu 15.04 is not shutting down on MacPro Retina 15,4&quot; 512gb"
date: 2015-10-22
forum: Apple Hardware Users
---

### Post by greg94 on 2015-10-22
I'll try to describe my situation. I installed Ubuntu 14.04 on Mac, and it was a lot of problems with hardware. Touchpad didn't work, no Thunderbolt hotplug, Wi-Fi issues, bad videodriver and etc. First of all i started to 'google' my problem. And I repaired completely Wi-Fi adapter only, others things didn't work correctly or didn't work at all. Then I suggest to upgrade my system to 15.04 with hope that it would be repaired automatically. It didn't help me at all. I thought that problem is in the old linux kernel and with not optimized building on Mac Hardware. So I build my customs kernels with full Mac Hardware support. I build 4.2.3 and 4.3.0 versions. Installed them, and what I see: touchpad was fixed, wi-fi works normally, but fglrx-driver didn't work corectly and I had to downloaded proprietary AMD catalyst driver and install it after removing fglrx. And with new kernel I received problem with brightness. I cant to change it anymore. But in 3.19 kernel I can. 
So - my goals are: 
1) To teach my iUbuntu to shut down without pushing Power buttom 
2) Fix brightness in 4.* kernels
3) Fix Thunderbolt hotplug

Community please help with advices. Only together we can beat this Mac Hardware

---

### Post by berglh on 2015-10-23
Exactly the same issues with MacBook Pro 11,5 (Mid-2015) with the AMD graphics and Ubuntu 15.10 on 4.2 kernel.

1) No Brightness Control
2) Wireless drivers from firmware 1.149 work but has no 5 GHz support
3) Multi-touch gesture support on the touch pad
4) Closing screen lid causes system to freeze (similar to power off bug)
5) Thunderbolt hot plug causes display manager to freak out
6) fglrx driver causes system to fail boot, I haven't tried the catalyst driver installer yet
7) Power Off bug, system never powers off, system fans reach 100%
       Note: After trying systemd & XHC1 disable I still experience unresponsive system

There are a few fixes to try here **@greg94**: [http://ubuntuforums.org/showthread.php?t=2299760](http://ubuntuforums.org/showthread.php?t=2299760)

---

