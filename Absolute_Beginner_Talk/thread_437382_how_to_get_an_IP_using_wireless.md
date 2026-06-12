---
title: "how to get an IP using wireless"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by ex625 on 2007-05-08
Hi - 
I have a WUSB54GC wireless dongle, with a simple, default install of Ubuntu.  (i.e. no ndiswrapper) networkmanager detects the wireless link and sees the ssid, but for some reason will not get an IP.  lsusb shows correct. iwconfig shows a wlanmaster0, and wlan0.   this is different than other dist installs; i've never seen this wlanmaster0 before; maybe or maybe not part of my problem? I have tried dhclient and dhcpcd, and they also seem to get hung up on this wlanmaster0.

bottom line question - is there a way to force it to go get an IP through wlan0?  

thanks-
ed

---

### Post by bobplano on 2007-05-08
can't you just assign it an IP address yourself? that would make it easier for you.

---

### Post by srt5 on 2007-05-08
I once got a wlanmaster using fedora and didn't know what it was, i think it turned out to be the receiver for my wireless mouse!

---

### Post by ex625 on 2007-05-08
hmm. static IP. hadn't thought of that; I also require use a work laptop which requires DHCP. I didn't think I could mix modes in my gateway, so my destop (w/ wireless dongle) would be static and laptop be dynamic. But I will check.
thanks for the suggestion.

-ed

---

### Post by ex625 on 2007-05-09
finally got it up using the instructions from here:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

basically, had to compile/install the serialmonkey rt73 drivers, blacklist the other ralink drivers that are automatically loaded,  and remove networkmanager.  The link has  good step by step instructions.

thanks for the help - 

-ed

---

