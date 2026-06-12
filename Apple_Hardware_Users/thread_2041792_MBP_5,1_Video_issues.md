---
title: "MBP 5,1 Video issues"
date: 2012-08-13
forum: Apple Hardware Users
---

### Post by SwedishWings on 2012-08-13
Anyone managed to get video to work properly on MBP 5,1? I tried both 32 and 64 bits 12.04 under both grub-pc and grub-efi, all combinations render artifacts and some flickering, in particular when dragging windows between work-spaces. Sometimes the lower 40 pixels or so are distorted, which looks like video memory corruption(?).

I tried all NVidia drivers i can think of; current, x-swat and the 304.32 beta from NVidia, all render artifacts.

I have the same problems with both 9600M and 9400M, though it seem slightly better on 9600. It makes no difference if i disable either in grub with outb xx commands.

I should mention that the stock NVidia drivers under 11.10 works perfect as does OS X, so it's likely not  hardware issues.


Any help here would be appreciated!

Regards,
Mike

UPDATE: I found a partial solution, [please check this thread]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/862430") if you have similar problems.

---

