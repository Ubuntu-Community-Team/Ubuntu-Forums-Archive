---
title: "Cannot connect to mesh WiFi network"
date: 2019-03-02
forum: Apple Hardware Users
---

### Post by mustdobetter2 on 2019-03-02
Hello,

I've installed Ubuntu 18.04 with 4.20 kernel on a MacBook Pro TouchBar 2016 (13,3). The WiFi card has automatically been picked up and drivers installed. I have been able to connect to an iPhone hotspot, but not to my home Mesh network (Tenda MW3). It's recognised but for some reason won't connect and keeps asking for the password. I've attempted to update the firmware as per the Broadcom guide, but to no avail. 

The output of the wireless helper script is here: [http://paste.ubuntu.com/p/kh2yK4xwKK/](http://paste.ubuntu.com/p/kh2yK4xwKK/)

Any help much appreciated!

---

### Post by jeremy31 on 2019-03-02
Moved to Apple Hardware

---

### Post by mustdobetter2 on 2019-03-02
> **jeremy31 said:**
> Moved to Apple Hardware

Whilst I understand the thought process in moving this under the Apple forum, it is more related to Broadcom driver support, and is not Apple-specific. I believe I'm more likely to get an answer under the original networking forum. Can I please request that this be moved back?

---

### Post by jeremy31 on 2019-03-02
I think you should look at [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
The first command will disable the wifi power management that causes issues, and if the network you are trying to use has TKIP enabled, yikes

---

### Post by mustdobetter2 on 2019-03-03
> **jeremy31 said:**
> I think you should look at [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
The first command will disable the wifi power management that causes issues, and if the network you are trying to use has TKIP enabled, yikes

Thanks, I've tried this and a huge amount of other steps but with no success. Doing a significant amount of reading on the subject I'm coming to the conclusion that this Broadcom adapter is just not going to work well enough (or at all) on Ubuntu. I can't find any reports of anyone having got this working consistently :(

---

