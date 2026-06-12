---
title: "Pre-install CD check detects errors in iso image"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by camelofdk on 2007-05-12
I downloaded the 64-bit desktop Dapper Drake 6.06.1 LTS iso image via WinXP and verified its md5 checksum using md5sum under SuSE Linux. I downloaded Infra Recorder to WinXP and used it to burn the iso image to a blank CD. Ubuntu will boot from the CD, but I haven't attempted to install Ubuntu because the pre-install "check CD" function tells me the CD causes read errors. The PC is a dual-boot WinXP/SuSE with an AMD Sempron 3000+ CPU with x86-64 support. (The SuSE 9.1 is installed as 64-bit.) My questions: 1. Is the Sempron a big problem in 64-bit mode?  2. Is 32-bit mode a better choice for it?  3. Is there any way to verify that the iso image was burned correctly?

---

### Post by taurus on 2007-05-12
Probably try to burn it at a slow speed like 4x.  Why not burn that ISO image in SuSE with k3b?

---

### Post by camelofdk on 2007-05-12
It burned for a while at about 16X, then magically throttled up to about 23X. (That program Infra Recorder doesn't offer a manual speed control.) Visually, the CD appears to be burned for only about 25% of its capacity. It shows weird properties data: in WinXP, 733,751,296 (699MB) used, 0 unused, but Infra Recorder seemed to think it had about 1.5 GB (sic) unused. (Yes, it's a CD, not a DVD.) But let me try k3b and see what happens.

What about the Sempron 64 ?   Is is usable for Ubuntu or a disaster ?

---

### Post by starcraft.man on 2007-05-12
> **camelofdk said:**
> It burned for a while at about 16X, then magically throttled up to about 23X. (That program Infra Recorder doesn't offer a manual speed control.) Visually, the CD appears to be burned for only about 25% of its capacity. It shows weird properties data: in WinXP, 733,751,296 (699MB) used, 0 unused, but Infra Recorder seemed to think it had about 1.5 GB (sic) unused. (Yes, it's a CD, not a DVD.) But let me try k3b and see what happens.

What about the Sempron 64 ?   Is is usable for Ubuntu or a disaster ?

Just use a 32 bit version of Ubuntu, there still really isn't a compelling reason to use the 64 bit version far as I see. Maybe in a decade when the world moves away from 32 bit processors and all the programs are coded natively to 64, if it ever happens...

---

### Post by camelofdk on 2007-05-12
Yeah, we had problems a couple of years ago at the Salt Mine when we upgraded some Sun machines to the 64-bit version of Solaris  -  a lot of loose ends.  Thanks for the tips.

By the way, if that iso burner (Infra Recorder) only works half the time, I think you guys need to recommend an alternative.  It's discouraging (especially for neophytes) to bomb out on a first attempted installation just because some bozo didn't know how to program a critical installation tool.

---

### Post by taurus on 2007-05-12
If you must use a burner in XP, try CDBurner XP, [http://www.cdburnerxp.se/](http://www.cdburnerxp.se/).

---

### Post by starcraft.man on 2007-05-12
> **taurus said:**
> If you must use a burner in XP, try CDBurner XP, [http://www.cdburnerxp.se/](http://www.cdburnerxp.se/).

Ummm, I think what he meant taurus was that he had gotten it burned with K3b and that maybe we should pick another program instead of infra recorder, since he and I believe a few other people had trouble with it. Not my department to change that entry though... up to you and other folks than I, I'm just a lowly Zealot in the Army of Ubuntu :D

---

