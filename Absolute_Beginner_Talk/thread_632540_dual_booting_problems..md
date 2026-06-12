---
title: "dual booting problems."
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by circaender on 2007-12-05
ok, so i have xp and ubuntu on my computer now, but now Grub is not coming up to let me choose..
and when i do get on ubuntu, it loads the orange bar to about the third bracket and hangs there..it was my frist load so maybe it was trying to configure my cards and things?..

---

### Post by Peryl on 2007-12-05
it might be something that has to do with ur motherboard config/ are both xp and ubuntu loaded onto the same drive? or seperate ones? if u dont have any important files i would just do a fresh install/ or boot with the Live CD and then check your ubuntu configs are

---

### Post by quandary on 2007-12-05
Read this:
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by bumanie on 2007-12-05
I had no trouble dual booting off the one drive, however when I installed a second drive to run feisty from, I ran into grub problems 13 and 17. In the end I went for the slightly less convenient option of loading windows on master primary, unplugging that while installing ubuntu on master secondary. Depending which OS I want, I just alter boot order in bios.

---

### Post by quandary on 2007-12-05
> **bumanie said:**
> I had no trouble dual booting off the one drive, however when I installed a second drive to run feisty from, I ran into grub problems 13 and 17. In the end I went for the slightly less convenient option of loading windows on master primary, unplugging that while installing ubuntu on master secondary. Depending which OS I want, I just alter boot order in bios.

grub mixes up hd numbers, that's why...

---

### Post by circaender on 2007-12-05
ubuntu is on my hard drive, the problem is..i can not get to it because grub will not come up.. I tried booting it from the bios but it just has my one hard drive..not its partitions.. so when i boot from it, it goess to windows..

---

### Post by quandary on 2007-12-08
> **circaender said:**
> ubuntu is on my hard drive, the problem is..i can not get to it because grub will not come up.. I tried booting it from the bios but it just has my one hard drive..not its partitions.. so when i boot from it, it goess to windows..

It seems you have installed Grub on the wrong partition. Get SuperGrub to repair that.

---

