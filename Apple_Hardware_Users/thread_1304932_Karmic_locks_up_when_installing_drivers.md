---
title: "Karmic locks up when installing drivers"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by underoathmatt on 2009-10-29
I have a late 2009 MBP 13" Unibody and I installed Karmic today.  I already had OS X 10.6 (Snow Leopard) and Windows 7 running on my machine.  I made two partitions for Ubuntu one mounted at / and one at /home.  The install went fine.  When I went to install the proprietary drivers, I installed the Broadcom wireless driver and then went to install the NVIDIA graphics driver and when the window popped up asking for my password the computer locked up and would not respond to anything.  I let it sit for a while thinking it was loading but nothing happened.  I held the power button and shut down my computer and now when I try to boot into it, I get a kernel panic error.  Anyone else having this problem or know of a fix for it?  

Note: My roommate was installing Karmic Kubuntu on his mac (same model as mine) and his locked up at the same point and he shut his computer down and now he is getting the same error.

Thanks.

---

### Post by frigginacky on 2009-10-29
I have the exact same problem after doing the exact same actions on a Dell XPS M1330.  No idea what the fix is though. :(

---

### Post by underoathmatt on 2009-10-29
I figured it out.  Instead of installing the video driver through the built in driver manager, open terminal and type

sudo apt-get install envyng-qt
insert Password
when that finishes type:
envyng -k

That should install your video drivers.

---

### Post by frigginacky on 2009-10-29
Worked like a charm.  Thanks!

---

### Post by Nadav34 on 2009-11-14
> **underoathmatt said:**
> I figured it out.  Instead of installing the video driver through the built in driver manager, open terminal and type

sudo apt-get install envyng-qt
insert Password
when that finishes type:
envyng -k

That should install your video drivers.

Hi, I also have a similar problem. I went to ATI's website to download the linux radeon 4870 driver for my mac pro. Will the above also help me to install the appropriate drivers as well? Strange though under display settings, my monitor is recognized as UNKNOWN instead of Apple Cinema Display(24 inch LED)?

---

### Post by frigginacky on 2009-11-14
I believe envyng works for ATI drivers too, so you might as well give it a shot.

---

### Post by JairunCaloth on 2009-11-21
I had a very similar problem with my MBP 4,1

I tried to install the video and wifi drivers through the hardware devices interface. My system hard locked and didn't come back. Afterwards, I could not boot.

I was able to boot into recovery mode, and install envyng-core
ran envyng -t (for text mode). Un-installed the Nvidia driver, reinstalled, rebooted and everything is good :)

---

