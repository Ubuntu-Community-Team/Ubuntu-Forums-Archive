---
title: "90% wifi speed reduction with b43 driver, mbpro 5,3, can't install wl module"
date: 2012-11-26
forum: Apple Hardware Users
---

### Post by adivparadise on 2012-11-26
So I've been hunting through the forums and the web, trying to see if anyone has encountered this problem and found a solution. While I've found a few others with the same problem, I haven't found anyone with a solution.

I have a MacbookPro 5,3 running a nearly fresh install of Bodhi Linux 2.1.0 (which is basically Ubuntu 12.04 running the Enlightenment desktop, and is probably closest to Lubuntu, but for the sake of being technically correct, is just based on Ubuntu). Almost everything works beautifully. However, my internet connectivity is crap. The ethernet doesn't connect at all, and I'm seeing a speed reduction in my wifi of 90% or more--a network that gives me 35 mbps on Mac OSX and on a different laptop running the same distro gives me 0.8 mbps on Bodhi (Ubuntu) on the mbpro. A network that gives 12 mpbs gives me about 1 mpbs. I've tried replacing the b43 driver with the Broadcom STA driver (wl), both through bcmwl-kernel-source and through the broadcom-sta-common and broadcom-sta-source packages, and neither has worked. With both scenarios, ```
sudo modprobe wl
``` outputs ```
FATAL: Module wl not found.
```

Anyone have any insights as to how to get this dang thing working? I love this beautiful piece of hardware, and I'd really much rather use linux on it than Mac OSX.

**The machine:**
*Macbook Pro 5,3
*BCM4322 wireless card
*b43 driver installed

**The OS:**
*Bodhi 2.1.0 (Ubuntu 12.04, with some Lubuntu elements)
*Installed 3 days ago

---

### Post by adivparadise on 2012-11-28
Okay, I figured it out. Turns out this is a bug in the Broadcom driver source code for the B43xx chips for all kernels 3.4 and higher. You can view the bug report here: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/994255]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/994255")

Some enterprising user put together a patched version of the driver, to be found here: [https://launchpad.net/~eugenesan/+archive/ppa/+sourcepub/2438281/+listing-archive-extra]("https://launchpad.net/~eugenesan/+archive/ppa/+sourcepub/2438281/+listing-archive-extra"). This patch appears to have been incorporated into the main release for Ubuntu 12.10 (Quantal).

I simply downloaded and installed the appropriate .deb, and ran the following:
```

sudo rmmod brcmsmac
sudo rmmod bcma
sudo rmmod b43
sudo rmmod wl
sudo modprobe wl

```
Reboot, and the wl module loads up automatically, and the wifi works beautifully and quickly.

This thread should now be marked solved.

---

