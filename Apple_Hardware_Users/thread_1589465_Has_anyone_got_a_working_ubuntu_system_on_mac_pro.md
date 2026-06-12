---
title: "Has anyone got a working ubuntu system on mac pro?"
date: 2010-10-06
forum: Apple Hardware Users
---

### Post by hyperfunctions on 2010-10-06
Has anyone got a working ubuntu system on mac pro? Which one distro and version etc..?

I'm asking because I want to use ubuntu but I cannot find the right one for my computer hardware.

thanks for your help

---

### Post by sanderd17 on 2010-10-06
[https://help.ubuntu.com/community/MacBookPro]("https://help.ubuntu.com/community/MacBookPro")

I've never read about problems with installing ubuntu on a mac. Did you look at the above link?

---

### Post by hyperfunctions on 2010-10-06
> **sanderd17 said:**
> [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

I've never read about problems with installing ubuntu on a mac. Did you look at the above link?

yeah but it's about a different type of computer and I haven't had luck with the suggestions on that page

---

### Post by theverant on 2010-10-06
I have a dual boot 4 core Nehalem (early 09) Mac Pro (desktop).  This is the generation previous to current.  I have the ATI 48xx graphics card, which should be very similar to the new 5xxx card.  No major problems that I recall, though I've just been using Virtualbox most of the time for the past year.

What was your issue?

---

### Post by efflux on 2010-10-07
I have a Macbook Pro 4.1 ad it is impossible to install any version of Linux on it. I have tried every which way.

---

### Post by linuxopjemac on 2010-10-08
Tnis is the start page, it's outdated and not well maintained. So you are on your own a little.
[https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)

I have a Fedora instalaltion for you:
[http://blog.christophersmart.com/2009/12/02/how-to-triple-boot-mac-pro-with-os-x-fedora-windows/](http://blog.christophersmart.com/2009/12/02/how-to-triple-boot-mac-pro-with-os-x-fedora-windows/)

---

### Post by trevolio on 2010-10-10
I have a macbook pro and got it working correctly on ubuntu 10.04. used disk utility from mac to partition, then turn off your computer turn back on holding the alt/option key. insert your disk and boot from it. when it gets going go through normally tell you get to partitions do manual click to install into your newly partitioned area make it ext 4 and / also make a swap (atleast 2gb) then install.

---

### Post by cha0s_unity on 2010-10-11
It may be a little redundant but try using boot camp to make a partition for Ubuntu. Then boot from an Ubuntu live cd. When you are in the install process manually control the partitions. Delete the partition boot camp and replace it with an ext4 partition. You probably don't have to make it with boot camp first but I did it this way just in case OSX didn't want to play well with the new partition made by Ubuntu.

---

