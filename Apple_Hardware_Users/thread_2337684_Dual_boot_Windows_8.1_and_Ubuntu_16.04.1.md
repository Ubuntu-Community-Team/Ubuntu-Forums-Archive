---
title: "Dual boot Windows 8.1 and Ubuntu 16.04.1?"
date: 2016-09-20
forum: Apple Hardware Users
---

### Post by Robert_Jackson on 2016-09-20
OK.

Its time to upgrade to 16.04.1 because the NVidia TX-1 now support its.
So the goal is windows 8.1 on one partition and Ubuntu 16.04 on another partition with no OSX.

I started with loading 16.04.1 by its self across the entire disk with no windows and no OSX as a base line just to make sure I had a work baseline to reference against.
I just finished it last night.
Tonight I will wipe the drive clean and follow my own instructions from my "Dual boot Windows 8.1 and Ubuntu 16.04.1" and see if I can get it to work.

---

### Post by T.J. on 2016-09-20
> **Robert_Jackson said:**
> OK.

Its time to upgrade to 16.04.1 because the NVidia TX-1 now support its.
So the goal is windows 8.1 on one partition and Ubuntu 16.04 on another partition with no OSX.

I started with loading 16.04.1 by its self across the entire disk with no windows and no OSX as a base line just to make sure I had a work baseline to reference against.
I just finished it last night.
Tonight I will wipe the drive clean and follow my own instructions from my "Dual boot Windows 8.1 and Ubuntu 16.04.1" and see if I can get it to work.

In order to get things to work in any kind of dual boot configuration, Windows has to be installed first, usually on the first data partition of the drive - otherwise it will not function properly.  You will need to then reserve space for the other operating systems you wish to boot, and you should install Linux last.  The problem is that the Windows bootloader is very sensitive, and does not like to cooperate with other systems.

If it is the Nvidia TX-1 board that I have read about, it has an Tigra ARM processor. Linux compiled for ARM will work, but regular Windows 8.1 will **not** work. Windows is made for Intel and AMD processors.  You would need Windows RT for ARM, and so the discussion is pretty much moot.  If the board is something else with an x86/x64 processor, it should be possible if the firmware is up to it - but from what I have read of the TX-1, it appears to me that Nvidia only expects Linux to work.

---

