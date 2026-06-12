---
title: "Internet randomly stops working."
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-11-27
Hi, I am using a Gateway laptop with a Broadcom 43xx wireless card. I used the firmware installer and I am able to use the wireless, but it will randomly stop working. My computer still recognizes the networks around the area, but I can not connect to any of them. Also, when the internet stops working the computer still shows a signal and tells me that I am connected.

Any ideas? Thanks a lot.

---

### Post by DSn0wMan on 2007-11-27
I would guess that its either a problem with the firmware, or driver. I would try either upgrading, or downgrading the firmware.

---

### Post by st33med on 2007-11-27
Also, could you please post the output of:
```
lspci | grep Broadcom
```

---

### Post by kevindubrow on 2007-11-27
Here we go:
~$ lspci | grep Broadcom
08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Also, how would I o about downgrading the firmware? Thank you both for your responses!

---

### Post by DSn0wMan on 2007-11-28
It seems that the BCM4318 behaves a little differently than other BCM43XX models. So I am thinking it's probably a driver issue. Take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

---

### Post by kevindubrow on 2007-11-28
This looks like it is going to work! Thank you so much for finding this for me! I'll tell you the result when I am able to do this on my computer at home.

---

