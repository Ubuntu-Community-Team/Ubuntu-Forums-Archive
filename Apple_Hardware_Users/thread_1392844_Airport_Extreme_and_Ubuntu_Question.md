---
title: "Airport Extreme and Ubuntu Question"
date: 2010-01-28
forum: Apple Hardware Users
---

### Post by jml on 2010-01-28
I have a 12" G4 Mac PowerBook.  With an Airport Extreme wireless (Broadcom chipset) card.  I am researching the issues involved with installing Linux on this machine.  Only one obstacle remains, wireless functionality.  According to what I have read, Linux is now able to recognise and enable the wireless card in my PowerBook.  Unfortunately, it will only support the 802.11b protocol and not 802.11g.  This is a deal breaker for me as I need to access 802.11g only wireless networks.  Is anyone aware of a way to get Linux to support 802.11g?  Even Yellow Dog Linux, (the commercial, non-free distro,) does not support 802.11g,  Any help would be appreciated.  Thanks in advance.

Joe

---

### Post by linuxopjemac on 2010-01-28
I read this:
> 
      b43 driver for modern BCM43xx devices. This driver supports the new BCM43xx IEEE 802.11G devices, but not the old IEEE 802.11B devices - those are supported by the b43legacy driver. This driver uses V4 firmware, which must be installed separately using b43-fwcutter (commit) 

[http://old.nabble.com/Looking-for-HOWTO-use-airport-extreme-with-recent-kernels-td15248256.html](http://old.nabble.com/Looking-for-HOWTO-use-airport-extreme-with-recent-kernels-td15248256.html)

#
# bcm4306 (Rev. 2 uses b43legacy, Rev. 3 uses b43) 

If you have Rev. 3, then you are in business...check it out with
```

lspci -vnn | grep 14e4
```

see at [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

You can just go in a liveCD environment and check this all out.

---

### Post by collegestudent on 2010-02-09
First off, hi all.  This is my first post and I am a newby to Ubuntu.  I just dowloaded 9.10 onto my PowerBook G4, 12", 1.2GHz, 512MB Ram.  So far so good.  One big issue I had was connecting to the internet.  I browsed quite a few posts on the internet, all relating to older versions of Ubuntu.  But I have since gotten it working.  The easy fix, I jumped into system/administration/synaptic package manager and reinstalled the broadcom b43-fwcutter.  Just select re-install and apply.  The package reinstalls. I also downloaded the wi-fi radar.  I don't know if that really did anything, but since I did those two at the same time I am not sure what happened.  Also, the night before, I downloaded updates with the Update Manager.  Trying to fiddle with the wireless on the Terminal just didn't work out.  I am guessing that the developers have gotten it figured it out and I just needed to update the version that I downloaded.  Hope this helps. Good luck.  Now I need to get this battery issue figured out.

---

