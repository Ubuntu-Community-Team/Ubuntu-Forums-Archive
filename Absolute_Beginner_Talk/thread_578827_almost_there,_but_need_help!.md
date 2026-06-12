---
title: "almost there, but need help!"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by pyrplhaze on 2007-10-17
well, I have been having issues with my install, but I just got it working.  Here is what the problem was

"We later compiled the 2.6.22 and 2.6.23 RC1 kernels (using the kernel source from kernel.org), and verified that an 8139too module compiled with the default MMIO access allowed causes the boot process to hang, and loading the SDHCI module also causes the boot process to hang."

I have no idea what that is saying, but someone came up with an install disc that allowed these processes to be bypassed, I guess...his quote- "It doesn't contain the SDHCI module and a 8139too module compiled for PIO only access."

So, I download the .iso, run the install, and WHOOPEEE!!  It finally worked.  So, I restart, then I install the 141 updated it requests me to do, and restart once again.

Ubuntu did not boot.  THe boot screen comes up, but the progress bar was stopped, after just barely starting.

I am so close...does anyone have a clue what I could have updated that caused this?  It rebooted just fine before all the updates were installed......

HELP!!!!!

Thanks!

---

### Post by jingo811 on 2007-10-17
> **pyrplhaze said:**
> well, I have been having issues with my install, but I just got it working.  Here is what the problem was

"We later compiled the 2.6.22 and 2.6.23 RC1 kernels (using the kernel source from kernel.org), and verified that an 8139too module compiled with the default MMIO access allowed causes the boot process to hang, and loading the SDHCI module also causes the boot process to hang."

.....
.....
......

Ubuntu did not boot.  THe boot screen comes up, but the progress bar was stopped, after just barely starting.

I am so close...does anyone have a clue what I could have updated that caused this?  It rebooted just fine before all the updates were installed......

HELP!!!!!

Thanks!

I'm thinking that you might have problems because you are working on some latest kernel version which must make it unstable or something.
Because when I check my Ubuntu kernel version it's way older than your version and Synaptic haven't recommended any kernel updates for me yet to the same version as you are using.

```
wacko@jacko:~$ uname -r
**2.6.20-16-generic**
```

---

### Post by pyrplhaze on 2007-10-17
josh@josh-laptop:~$ uname -r
2.6.20-15-generic


I think I am going to just try process of elimination...go one by one on all 141 updates...and see what happens.  should make for an interesting night!

---

