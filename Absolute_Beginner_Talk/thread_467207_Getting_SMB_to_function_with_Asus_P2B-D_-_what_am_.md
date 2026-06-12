---
title: "Getting SMB to function with Asus P2B-D - what am I doing wrong?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by waynemr on 2007-06-07
I started making the switch to Ubuntu about a week ago, and it is actually quite fun! I currently have an Asus P2B-D with dual PIII 500MHz processors and 512MB of RAM and an ATI Radeon 7000 LE. Anyway, Feisty loaded up on the system with zero problems, right off the bat, and it was rock solid. Well, zero problems except that it did not detect the second CPU. This board has the Intel 440BX chipset and the last BIOS released for it.

So, I went looking through the forums and found out that to enable the second processor, I had to use the "SMB" version of the distribution. To do this, I fired up synaptic and searched for "linux image smb" and it came up with a couple of different flavors. I selected the most generic and highest version 386 version and marked it for installation.

Once installed, the system came up about two thirds of the time, but the other third of the time would hang at different places (no pattern I could see). Once up, I checked and found that both processors were working, but the system would randomly hang when idle or doing things. It would always hang, if I tried to run the disk administrator.

Seeing as how the system was completely rock-solid when running on just one processor, I am guessing I either did something wrong when installing the SMB image, or the 440BX chipset just doesn't work well with the SMB image I was using.

I've since wiped and reinstalled Feisty on the box and am running it in single processor mode as a web server. Ultimately, I would like dual processor functionality.

- Has anyone had any success with getting SMB support on an Asus P2B-D with Feisty? 
- How about other 440BX based motherboards?
- Can someone post or link to a step-by-step set of instructions for using the SMB image?
- Actually..., if I enable the SMB-capable image in synaptic, do I need to remove the non-SMB images?

Thanks!

---

### Post by waynemr on 2007-07-25
I still have not located a good answer for this online any place. Has anyone else come across this issue?

---

### Post by DiabboVerdde on 2007-11-21
you mean SMP, right ? this means symmetric multiprocessor. search for SMP versions of the kernel in old ubuntu versions, or just install gutsy gibbon, that will authomatically detect both processors. I use the same P2b-D you use.

Regards,

Geoff

---

