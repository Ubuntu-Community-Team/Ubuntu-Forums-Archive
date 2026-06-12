---
title: "Dual Boot Problem (Vista/UbuntuStudio7.10) on Laptop"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by thenewbeat on 2007-10-26
Hello, I've got an HP dv9000 Laptop with an AMD 64x2 Processor, 2 GB RAM, & 2 120 GB Hard Drives. 

One has a factory install of Vista (32bit), the other was empty. So, I wanted to install the new Ubuntu Studio on the second drive. 

I installed the AMD 64bit version on the second drive without any problems. But, when it came time to startup the OS for the first time the screen froze (about 1/3 of the way through the splash screen status bar). 

I thought "maybe it's the 64bit version", so I did a reinstall using a new iso with the regular Intel x86 version. Once again everything installed fine, but when i tried to run the OS it froze on the splash screen (this time about half way through the status bar). Then it went to some error screen (and of course I didn't write down the error). It looked like it was trying to to run some test, but it froze too. 

I am still able to run Vista, although it doesn't recognize my second hard drive now, but I think that's normal? Any suggestions?

-Robert

---

### Post by thenewbeat on 2007-10-26
when i restarted my laptop (to repeat the error so i could write it down) i get a new error when GRUB is loading. the screen says:

```
GRUB loading stage 1.5.

GRUB loading, please wait...
Error 17
```

so, now the computer is complete down. Anyone?

-Robert

---

### Post by thenewbeat on 2007-10-26
OK, so i figured out the Error 17 deal... but now i have the Ubuntu Studio Startup Error:

Here's what's on the screen:
```

 * Reading files needed to boot...     [ok]
 * Preparing restricted drivers...      [ok]
 * Setting the system clock
 * Staring basic networking...          [ok]
 * Starting kernal event manager...  [ok]
 * Loading hardware drivers...         [ok]
 * Setting the system clock
 * Loading kernal modules...          
 * Loading manual drivers...           [ok]
 * Activating swap...                       [ok]
 * Checking root file system...
fsck 1.40.2 (12-Jul-2007)
/dev/sdb1 has gone 904 days without being checked, check forced.
/dev/sdb1: |==========                                    -17.7%

```

after about 1 minute it stopped at 17.7% (same as las time). 

Anyone out there?

---

