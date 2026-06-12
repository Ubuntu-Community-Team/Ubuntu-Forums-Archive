---
title: "JMicron PATA Controller/Ubuntu 7.04"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by jdietz on 2007-04-20
I cannot get my PATA DVD drive to work in Ubuntu.
With my HDD (Just 1 in the system) plugged into the JMicron SATA port, and the DVD drive plugged into the JMicron PATA port (The only one on my board), I installed 6.10 off of the live CD.  No problems during install.  I booted from the HDD for the first time and I could not mount the CD rom.  I get a "Cannot mount device" error.

Last night I updated to 7.04 from update manager.  No improvement in PATA port or DVD drive function.  Just for fun I put the 6.10 live CD in and it still works.

I looked at the following thread: [http://ubuntuforums.org/showthread.php?t=234706&highlight=jmicron](http://ubuntuforums.org/showthread.php?t=234706&highlight=jmicron)
The thread is in tech-speak, has way too many posts (>250), and also I cannot make any sense of it (The thread covers the supposed "JMicron" problem).  It seems that this controller is supported in Ubuntu, otherwise I would not have been able to do the install with the only I/O devices connected to the JMicron.  How do I start diagnosing/fixing the problem?

My motherboard is the MSI P965 Platinum.  The board came with v1.3 firmware, the latest version is 1.4 firmware.  Looking at the vendor release notes, the changes between these versions appear to be cosmetic only (No functional changes).  Should I upgrade anyway?

---

### Post by kyphi on 2007-04-20
The P965 board does have quite a few quirks but they can be circumvented.  I have an Intel P965 board.

To get the DVD drive functioning  I used an IDE to SATA Converter.  It works very well and is cheaper than buying a new SATA DVD.

---

### Post by uputer on 2007-04-20
I'm thinking of buying a core 2 duo machine.   I'd be buying a SATA DVD drive and a SATA HD.   With this, would I be able to avoid the JMicron issues involved with linux on an Intel (Core 2 Duo) machine with the P965 (and 975X?) chipset?  

Can anyone tell me which Ubuntu version is best to use with such a machine?   The latest Feisty and at which version?

---

### Post by kyphi on 2007-04-20
Please note that I do not claim to be an expert in these matters.

What I can tell you is that using an Intel DG965WH board everything works fine for XP.  In Ubuntu 6.06, however, I had no DVD drives (2), these were IDE connected until I used an IDE to SATA adapter and plugged it into the SATA port.  That worked fine for one DVD but not the second one.  There also was no ethernet connection until I disabled the onboard chip and installed an ethernet card.  I have never been satisfied with onboard sound so that also was disabled and I installed a sound card.

The CPU is Dual Core and presents no problems in Ubuntu.

As to which version of Ubuntu to use - that is up to you.  I prefer a tried and tested approach and Ubuntu 6.06 is supported unti 2009.  It does everything I want to do.

---

### Post by jdietz on 2007-04-21
Using IDE-SATA adapter is a work-around, but I suppose it is necessary.  This doesn't really "Solve" the issue so I won't mark the thread solved just yet.

---

### Post by drtvasudevan on 2007-04-21
> **uputer said:**
> I'm thinking of buying a core 2 duo machine.   I'd be buying a SATA DVD drive and a SATA HD.   With this, would I be able to avoid the JMicron issues involved with linux on an Intel (Core 2 Duo) machine with the P965 (and 975X?) chipset?  

Can anyone tell me which Ubuntu version is best to use with such a machine?   The latest Feisty and at which version?

i have a dual core pc.
DG 965 RY chipset mobo
till the beta release installation was  problem.
but feisty alternate ubuntu was installed today with no problems with pata dvdrom.
used to install via the hard disk install till now.
tv

---

