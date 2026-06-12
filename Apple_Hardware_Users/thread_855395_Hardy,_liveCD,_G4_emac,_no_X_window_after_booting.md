---
title: "Hardy, liveCD, G4 emac, no X window after booting"
date: 2008-07-10
forum: Apple Hardware Users
---

### Post by baosheng on 2008-07-10
Hi,

I am trying to boot my G4 eMac from Hardy live CD. It looked fine until the moment the X window was supposed to start. But, I saw nothing on my screen. I have tried Fedora, same problem. Can someone tell me why?

Thanks.

---

### Post by avtolle on 2008-07-10
I was never able to get the Live CD to boot successfully on my G4 Cube. For what it's worth, I installed from the alternate install iso burned to CD-R at 4x, and once installed, had to manually edit my /etc/X11/xorg.conf file to get X to run. Luckily, I had a copy of my working file under 7.10 to which to refer to get xorg.conf set up under 8.04, which was done from the CLI. I think you may well be looking at a similar task, if you want to get 8.04 on the emac.

---

### Post by baosheng on 2008-07-10
well, the problem is, i even couldn't let 7.10 liveCD work. Thus, I have no workable xorg.conf

From information on Mac OS X, my graphic card model is ATI Radeon 9200, chipset model: ATY, RV280
Bus: AGP
vendor ATI(0x1002)
device id: 0x5962

---

