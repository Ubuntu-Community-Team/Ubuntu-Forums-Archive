---
title: "Sudden boot problems"
date: 2011-03-20
forum: Apple Hardware Users
---

### Post by skullmunky on 2011-03-20
I have a MBP (6,2) in a triple-boot setup, with Snow Leopard, Kubuntu 10.10, and Windows XP.  Everything's been working fine, all OS's boot and behave nicely, then suddenly today both Linux and Windows won't boot.  All three show up in the refit menu.  OSX boots fine.  Choosing Linux shows the gray penguin, then hangs on a black screen with blinking cursor.  Choosing windows shows the gray windows icon, then same hang on a black screen with blinking cursor.  The refit partition tools says the the GPT and MBR tables are synced, so no problem there.  I can also boot to an ubuntu live CD.  All partitions mount, everything's there, and fsck says they're clean.  Any suggestions?  Not sure what to try next.

---

### Post by srs5694 on 2011-03-21
Download the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/), run it from the live CD, and post the RESULTS.txt file it produces between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. This will tell us something about your partitioning and boot loader configuration, but it won't fix anything; it's purely a diagnostic tool, not a repair tool.

---

### Post by skullmunky on 2011-03-22
Thanks!  That script is great.  I found similar instructions in another thread and got it fixed.  The bootscript pointed out a problem with core.img.  I reinstalled Grub to the MBR and now everything's fine.  

It's funny, the process sounds scary but was actually very simple.  The key for me was the step after booting to a live CD where you mount the hard drive partition and chroot into it before doing grub-install.  
:KS

---

