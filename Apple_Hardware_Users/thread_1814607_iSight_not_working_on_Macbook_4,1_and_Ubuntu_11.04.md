---
title: "iSight not working on Macbook 4,1 and Ubuntu 11.04"
date: 2011-07-29
forum: Apple Hardware Users
---

### Post by KanadaKid on 2011-07-29
Hi all,

Although I had 11.04 running smoothly on my Macbook 4,1 (OS X 10.5) since it came out, I never bothered to actually test the iSight camera. So I fired up Cheese, but it claimed that it could not detect any webcam installed. gstreamer-properties does not list iSight either.

I followed this article step by step: [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight). After installing the firmware I pulled from my OS X partition, neither Cheese nor gstreamer picked up on my camera. As a matter of fact, I investigated further and realized that /dev/video0 does not even exist.

The firmware seems to be recognized by the kernel, according to dmesg:
> usbcore: registered new interface driver isight_firmware

I repeated the procedure in the article again after purging the firmware-tools package, but no dice. I resorted to booting back into OS X to use my webcam, but as you can imagine this is not very convenient heh. Does anyone have any advice as to where to go from here?
[B]
EDIT: I ended up uninstalling the firmwire, since it caused my Macbook to become unresponsive (purple screen of death?) every time after coming out of sleep. I haven't found a solution for that either. For now I guess I'll keep my OS X on a partition to use iSight until something comes up to resolve this issue. :/[/B]

Thanks!

---

### Post by MidnightRider617 on 2011-09-25
Hey,

I have the same issue, I'm not really sure how to solve this problem. If you've figured anything out since posting this, please let me know.

---

