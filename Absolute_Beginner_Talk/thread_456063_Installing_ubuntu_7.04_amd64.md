---
title: "Installing ubuntu 7.04 amd64"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by _mOrgoth_ on 2007-05-27
Now I am planing to install system in RAID 0 mode. My motherboard is DFI Lanparty 939.s with nv nf4 chipset that suports raid. I have some experience with installing windows in raid mode but on linux this is my first time. When I was installin windows I needed floppy with raid drivers, press F6 during installation and load them from floppy.
Can I install ubuntu amd64 in raid? What do I need to do that?
(I have 2 indentical ATA disk)

---

### Post by djgrandmarquis on 2007-05-27
[http://ubuntuforums.org/showthread.php?t=184934](http://ubuntuforums.org/showthread.php?t=184934)

I have a Socket 939 board as well. As far as I know, the nvraid driver is Windows-only. (It's not actually hardware Raid, it's software "fakeraid"). So I just used Linux's software Raid on ext3 and it works very well.

---

