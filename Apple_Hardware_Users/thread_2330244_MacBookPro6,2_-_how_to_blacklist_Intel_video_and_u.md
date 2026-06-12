---
title: "MacBookPro6,2 - how to blacklist Intel video and use only Nvidia"
date: 2016-07-09
forum: Apple Hardware Users
---

### Post by phil-xfr on 2016-07-09
Hi,

I have a 2010-ish MacBookPro6,2, which has hybrid Intel/Nvidia graphics.

Switching does not work - it black-screens if I enable the Nvida driver, so I have to use Nouveau, but Nouveau runs the GPU at full speed, resulting in an alarmingly hot machine and a lot of fan noise.

Can anyone clue me in as to how I might disable or blacklist the Intel side, so that I could use the Nvidia driver and benefit from its GPU clock control?

Do I need to somehow disable the mux as well in order to prevent it from trying to switch?

I am using Ubuntu Mate 16.04

Ta!

Philk

---

### Post by bryant-belarmino on 2016-10-08
I'm interested in knowing if this is possible too. I've tried some of the configs online and they all result in the black screens too. 

If I could add to your question, are you experiencing the graphic kernel panic attacks? I'm wondering if swapping to NVIDIA will cause this to occur in Ubuntu. Ubuntu saved this macbook pro and made it fully functional again, even letting me use an external monitor. 

If someone knows if turning changing to NVIDIA on a macbookpro6,2 causes the issue to appear again, i'll definitely look for another solution to the GPU dilemma.

---

### Post by gnwiii on 2017-01-01
I have a MacBookPro 6,2.  The well-known graphics problem didn't occur until after the warranty expired.  This is a work system and desktops at work use Linux Mint 17, so  I installed Linux Mint 17 (based on Ubuntu 14.04) but had to remove bumblebee and blacklist intel to use nouveau.  Under 14.04 I booted without X11 and ran startx manually.  The system ran hot with a lot of fan noise.  Watching videos caused it to overheat and shutdown.   Battery life is lower using nouveau compared to Intel, but even under macOS the apps I use keep the CPU busy.

A few months ago I updated to Mint 18 (Ubuntu 16.04). I use software from NASA that "calls home" to get current data.   On Dec. 23rd, 2016, NASA turned off their http servers due to US Gov't policy that dictates use of http.  In order to connect to NASA's shiny new https servers, recent versions of wget, curl, python 2.7 ssl, Java, and git are needed.  Suitable versions are available in Mint 18 (and Ubuntu 16.04).  A side effect of this upgrade is that the system boots to nouveau X11 and runs cooler with less fan noise.   There are some limitations related to openGL, and I have not tried viewing long videos.

For me, Linux Mint is Ubuntu with a lightweight desktop and an extra layer of quality control over updates, e.g., stabilized Ubuntu.   I am pleased that a system pronounced "dead" by Apple meets 90% of my needs.

To use nouveau, I followed some guidance I found on the internet: comment out the "blacklist nouveau" line in  ```
/etc/modprobe.d/bumblebee.conf 
``` and used aptitude to remove bumblee/optimus related packages.

---

