---
title: "To FreeBSD or not to FreeBSD..."
date: 2008-05-12
forum: BSD
---

### Post by cardinals_fan on 2008-05-12
I've used NetBSD for a while now, and I really like it.  Unfortunately, it just doesn't seem to get the same support as FreeBSD: no NVIDIA, no Opera (has to be run with Linux emulation), less software.  So what do you all think: should I stick it out, or move back to FreeBSD?

---

### Post by chachawpi on 2008-05-12
I've never tried NetBSD.  FreeBSD is a huge headache right now though:  

- USB devices all turn off on boot - they need to be manually unplugged and reattached to get recognized again
- I have to unplug my external hard drive or I get a kernel panic at boot
- NVidia drivers don't work w/ 4 GB of RAM (or so I'm told) and my system just hard locks or gives errors

---

### Post by cardinals_fan on 2008-05-12
> **chachawpi said:**
> I've never tried NetBSD.  FreeBSD is a huge headache right now though:  

- USB devices all turn off on boot - they need to be manually unplugged and reattached to get recognized again
- I have to unplug my external hard drive or I get a kernel panic at boot
- NVidia drivers don't work w/ 4 GB of RAM (or so I'm told) and my system just hard locks or gives errors
1. Not an issue for me
2. Also not a problem
3. I heard about the NVIDIA/64-bit problem.  It doesn't apply to me though.

---

### Post by MONODA on 2008-05-13
I think you shoudl go ahead and try it, it is quite nice but I suggest doing a minimal installation then building up from there, it gets frustrating switching cds during installations. Also, you could jut partition your hard drive in half and then remove the partition you dont want after you ahve make your decision.

---

### Post by cardinals_fan on 2008-05-13
> **MONODA said:**
> I think you shoudl go ahead and try it, it is quite nice but I suggest doing a minimal installation then building up from there, it gets frustrating switching cds during installations. Also, you could jut partition your hard drive in half and then remove the partition you dont want after you ahve make your decision.
I downloaded the first CD, as I understand it that one is enough for a minimal install.  No way I'm burning all three with my miserable burner!

My hard drive is partitioned with Zenwalk and NetBSD partitions.  NetBSD was simple to get to where it is now (ie working fine but no proprietary NVIDIA), so I'll probably replace it.  My one last try before switching to FreeBSD is to check out the 'work in progress' nvidia-freebsd package in pkgsrc-wip.

---

### Post by jrusso2 on 2008-05-13
I don't really see the point to running either of them on a desktop when Linux is so much better supported.

---

### Post by thedevnull on 2008-05-13
NetBSD isn't really focused at the desktop.  If you want BSD as a desktop try PC-BSD or DesktopBSD.  FreeBSD is of course always a great option.  I have to agree with what other people have said they are still very much behind Linux in the desktop space.

---

### Post by cardinals_fan on 2008-05-13
> **thedevnull said:**
> NetBSD isn't really focused at the desktop.  If you want BSD as a desktop try PC-BSD or DesktopBSD.  FreeBSD is of course always a great option.  I have to agree with what other people have said they are still very much behind Linux in the desktop space.
I have given many reasons in other posts why *BSD works better for me.  They include hardware support and stability.  I know that the proprietary NVIDIA drivers will work in 32-bit FreeBSD.  NetBSD is a lot of fun, but I think that it's time to move back to good old FreeBSD (I've used it before BTW).

---

### Post by MONODA on 2008-05-14
> I downloaded the first CD, as I understand it that one is enough for a minimal install. No way I'm burning all three with my miserable burner!

My hard drive is partitioned with Zenwalk and NetBSD partitions. NetBSD was simple to get to where it is now (ie working fine but no proprietary NVIDIA), so I'll probably replace it. My one last try before switching to FreeBSD is to check out the 'work in progress' nvidia-freebsd package in pkgsrc-wip.
I have installed freebsd twice, once was a minimal install and once it was a full kde install. I think that you will need discs 1-3 and the docs cd so that is 4. During installation, they will call the docs cd 0. You should partition your hard drive before installation. You will only need one blank partition which the installation cd will partition to its needs.

---

### Post by cardinals_fan on 2008-05-14
> **MONODA said:**
> I have installed freebsd twice, once was a minimal install and once it was a full kde install. I think that you will need discs 1-3 and the docs cd so that is 4. During installation, they will call the docs cd 0. You should partition your hard drive before installation. You will only need one blank partition which the installation cd will partition to its needs.
Why should I need all these discs?  I'm going with a minimal (command-line only) install.

---

### Post by cammin on 2008-05-15
You won't need them.

---

### Post by cardinals_fan on 2008-05-19
I momentarily switched back to FreeBSD.  But as soon as the installer booted up, I realized why I had left.  NetBSD was so much cleaner and more elegant.  So here's my decision: I will keep NetBSD around, and hope that NVIDIA releases drivers for it.  In the meantime, I'm trying OpenSolaris.  Wish me luck!

---

### Post by Sef on 2008-05-20
> I momentarily switched back to FreeBSD. But as soon as the installer booted up, I realized why I had left. NetBSD was so much cleaner and more elegant. So here's my decision: I will keep NetBSD around, and hope that NVIDIA releases drivers for it. In the meantime, I'm trying OpenSolaris. Wish me luck!

Good luck.  I hope all works out well for you.

---

### Post by factotum218 on 2008-06-10
If vmware server ran on it i would switch to it full time in a heart beat.

---

