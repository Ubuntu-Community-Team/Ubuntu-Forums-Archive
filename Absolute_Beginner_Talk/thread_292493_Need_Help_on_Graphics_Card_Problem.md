---
title: "Need Help on Graphics Card Problem"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Bahbuu on 2006-11-03
Hi, I'm a new ubuntu user and I just installed ubuntu 6.06 (I heard this one is safer and more stable compared to 6.10)

Here is some of my information first:
My Laptop - Sony VAIO VGN-SZ18GP
Processor - 1.83 GHz Intel Core Duo
RAM - 512MB
Graphics - NVIDIA GeForce Go 7400  OR  Intel integrated graphics
(2 different graphics, because Sony SZ can switch graphics card whenever I need more battery life or when I need more power for graphics, etc.)

**My problem:**
When I installed Ubuntu 6.06, I accidentally used the **Intel Graphics **instead of **NVIDIA** graphics.
After my installation (everything went smoothly) I rebooted my computer and tried switching to NVIDIA graphics
however, once I swtched to NVIDIA graphics, I can't boot up to Ubuntu anymore and it says I got some graphics error or something.

I was wondering whether anyone could help me out on this problem (because I want to be able to use NVIDIA graphics on Ubuntu) or would the only solution for me be re-installing the whole Ubuntu package while using the NVIDIA graphics?

Thanks!!!

Note: I also tried using Easyubuntu but i keep getting errors
"W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718"

Any help?

---

### Post by Ecthelion on 2006-11-05
> My problem:
When I installed Ubuntu 6.06, I accidentally used the Intel Graphics instead of NVIDIA graphics.
After my installation (everything went smoothly) I rebooted my computer and tried switching to NVIDIA graphics
however, once I swtched to NVIDIA graphics, I can't boot up to Ubuntu anymore and it says I got some graphics error or something.

I was wondering whether anyone could help me out on this problem (because I want to be able to use NVIDIA graphics on Ubuntu) or would the only solution for me be re-installing the whole Ubuntu package while using the NVIDIA graphics?


You can reconfigure your xserver using
```
sudo dpkg-reconfigure xserver-xorg
```

You may want to choose the generic driver instead of the nvidia one and then follow [this HOWTO]("http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia+dapper") to get the latest nvidia drivers working on dapper.

---

### Post by ReaderRat on 2006-11-05
KEY Public HowTo get....
          **[http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773](http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773)**

---

