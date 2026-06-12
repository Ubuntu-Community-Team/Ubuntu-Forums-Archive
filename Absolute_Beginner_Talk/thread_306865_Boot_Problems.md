---
title: "Boot Problems"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2006-11-25
about half the time i boot my ubuntu box it comes up with a white text/black screen error saying:
> Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key_

the underscore at the end blinks at ~2Hz if it makes a difference

but the thing is, i ctrl+alt+del and change no settings and it will work on the second time.

my computer specs:
Athlon 64 xp3200+
Asus A8n-VM-CSM mobo
WD300 30Gb HDD (found dumpster diving)
1Gb ram
Sony DRU-820A DVD-burner
Generic CD-ROM

the boot order is HDD then DVD-R, the third option is disabled

i am running the default BIOS, i cleared it when i upgraded to Ubuntu (x64 pro to ubuntu is DEFINITELY an improvement!!!) is it even possible to upgrade BIOS in ubuntu?

---

### Post by Tomosaur on 2006-11-25
Could be a temperemental hard disk. I would start backing stuff up just in case.

Try keeping a boot CD in the disk drive and setting that to boot first. If the CD boots fine all the time, then that would indicate something is wrong with your hard drive. If same thing keeps happening, it could well be a mobo/BIOS problem.

---

### Post by Sonic Reducer on 2006-11-25
i'll try that with the u64 disk i installed ubuntu with

---

### Post by jerrykenny on 2006-11-25
If that hd is ropy, then a good strategy would be to install ubuntu on a smaller (reliable) disk, then mount the 300gig on /mnt/multimedia . . . . ie put all your films & music stuff on it . . . but not system stuff

---

### Post by Sonic Reducer on 2006-11-26
its only a little 30gig i got dumpster diving from a pentium 1 with 1 PCI slot on the mobo (4 ISA slots though). basically a very old HDD.

i like ubuntu so much i'm going to buy a  big SATA drive to reinstall everything on and keep this IDE one as my pron drive in a removable bay.

---

