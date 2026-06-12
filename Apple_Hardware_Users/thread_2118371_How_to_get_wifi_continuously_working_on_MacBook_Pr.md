---
title: "How to get wifi continuously working on MacBook Pro"
date: 2013-02-21
forum: Apple Hardware Users
---

### Post by GraveMAL on 2013-02-21
I recently triple booted my 2011 13" MacBook Pro with Ubuntu 12.10. I am trying to get it so that the wifi network is automatically searched for and signed into but everytime I log on, I have to enter terminal command              

sudo modprobe b43

to get wifi enabled. Is there any way that I get it so that it searches for and signs in automatically or is this just something I have to deal with. Any other commands I should enter?

---

### Post by ksatta1 on 2013-02-21
> **GraveMAL said:**
> I recently triple booted my 2011 13" MacBook Pro with Ubuntu 12.10. I am trying to get it so that the wifi network is automatically searched for and signed into but everytime I log on, I have to enter terminal command              

sudo modprobe b43

to get wifi enabled. Is there any way that I get it so that it searches for and signs in automatically or is this just something I have to deal with. Any other commands I should enter?

Don't know why you have to manually load the module, but you can just put the line "modprobe b43" in /etc/rc.local. Then it'll be run on every boot.

---

### Post by GraveMAL on 2013-02-21
Cool thanks got it working

---

