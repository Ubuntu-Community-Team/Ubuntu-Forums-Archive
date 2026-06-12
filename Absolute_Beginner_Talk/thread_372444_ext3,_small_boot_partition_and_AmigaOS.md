---
title: "ext3, small boot partition and AmigaOS"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Docter on 2007-02-28
Hmmm... where to start.

Hello, I'm Lee, I avoided wintel for many years by sticking with AmigaOS but I was seduced by WinXP.

For a short time.

I always knew about linux, I remember it first coming out but never having a net connection at home I never tried it because I would be denying it's true usability. I got a net connection while using my XP box and didn't give it another thought, I just put up with the bloatware and incredibly illogical processes. Four days ago I heard about Ubuntu, I tried the LiveCD and was impressed to see it had accessed the internet through my network with no user conf required. I immediately set about creating a 20gig and swap partition. I installed from the non GUI installer without a hitch selecting the default filesystem for my boot partition (ext2); I admit I was under an illusion that I was able to use NTFS which it was already formatted in, I blame a dodgy youtube video I watched for some backround and this is why I never researched the filesystems.

Okay so to the rub... So I now know that ext3 is an ext2 filesystem with journaling, this is to avoid those long disk checks on boot up after a dodgy shutdown or somesuch. However, the eagle-eyed among you will have noticed that my boot partition is only 20gig and the disk check really isn't that annoying plus I don't intend to invalidate my hash-table on a regular basis. Converting to ext3 is a simple process but I really am not convinced I need the extra functionality and I am keenly aware that I am a beginner here (even though it rings many bells with amigaOS which I learned inside out) which is why I am putting this out there to those gurus who will be able to enlighten me. :P

Anyone got any adice for lil ole me?


PostScript:

Many people seem to feel that installing the extra functionality on linux is a complicated affair... wow does ubuntu prove them wrong. I wasn't expecting to have all my media and plugins and well-used win programs working so quickly. This is great testimony to the developers. Let's put it this way: my WinXP boot still exists but I haven't been in there since I installed Ubuntu.. actually I don't even know if it still works and I don't much care either.

I feel like I've come home :D

---

### Post by localuser on 2007-03-13
Hi Lee and welcome to the wonderful world of Linux and Ubuntu.

> **Docter said:**
> Converting to ext3 is a simple process but I really am not convinced I need the extra functionality...

Anyone got any adice for lil ole me?


Are you asking advice on whether or not you should convert to ext3?  As far as I understand it, and you seem to have picked up on it as well, ext2 is ext3 with journaling turned off.  I don't believe that ext3 is more stable than ext2, but it may be a tad slower (though I think this is insignificant).

i guess another question may be...."why *not* convert to ext3?  I don't see that journaling hurts anything, and it can only help.

---

### Post by dptxp on 2007-03-13
i read somewhere that EXT3 is preferred, do not remember why, but the point was well taken. put a search on ext3 vs ext2.
:guitar:

---

