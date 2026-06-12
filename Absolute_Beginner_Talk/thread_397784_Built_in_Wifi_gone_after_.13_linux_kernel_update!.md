---
title: "Built in Wifi gone after .13 linux kernel update!"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by mbs348 on 2007-03-31
Hi

New to Ubutunu here, but I thought I would give the new beta a shot.

I was just wondering if anyone else had the issue that after upgrading to the latest .13 linux kernal that they noticed that the built in wireless mod ceased to pick up wireless signals.  I have an intel PRO/set Wireless card which I have seen on this forum to be a bit of a problem, but the funny thing is, it must not be just the driver, because I installed Wifi Radar, which can still detect wireless networks, while the built in modual doesnt even have a place for me to "enable wireless" any longer.

If anyone was able to fix it, if you could let me know that would be sweet.


EDIT: However, the Wifi radar has some trouble picking up encrypted networks of any kind, but luckily I can still snag my neighbors to download (hopefully) a fix! 

Thanks so much!

Max

---

### Post by hyper_ch on 2007-03-31
I had a problem with the -11 or -10 kernel... I posted a bug on [https://bugs.launchpad.net/](https://bugs.launchpad.net/) (well, first I searched if it was already submitted - and it was) and I added my data... less than 48h later the bug was resolved iwth a new kernel :)

You may want to do the same...

(this was "my" wifi bug:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92742](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92742) )

---

### Post by hyper_ch on 2007-03-31
Addon: And for the time being that this bug exists, just boot into -12 :)

---

