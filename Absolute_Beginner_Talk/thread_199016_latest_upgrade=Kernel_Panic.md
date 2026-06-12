---
title: "latest upgrade=Kernel Panic"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by mrresalg on 2006-06-18
Hi!
Synaptic indicated that there was ap 78 upgrades to bee made for Dapper 6.06 LTS -DApper Drake., so i followed :rolleyes: . All in the official repos... so after been told to restart, i did..:---) 
THEN...Kernel panic unabel to  uncompress an somthing about crc error. I could not get the thing to work, nither in recovery mode,[-X  so... i opened the grub meny list and removed the new kernel lines (txt) and now my ubuntu dapper starts again, but with the previous kernel, not the new one...  as a beginner in problem solving and managing of my system i wonder, what have i done! And why did not the upgrade work... :?:

---

### Post by kane77 on 2006-06-18
well when you upgrade a kernel it's allways a good idea to leave one or two older ones that you know that work for a case like this one... 
what happened is that the crc failed = probably a bad download... so try once again...

---

### Post by sandpaperback on 2006-06-23
I'm kind of having the same problem as well.  When I try to boot Dapper, I am suddenly getting a "CRC Failed" error when it tries to expand the kernel.  If I hit "e" on the GRUB screen and choose "boot" at the bottom of the list, it works fine.  The really strange part is I tried booting from the same CD that I used to install Dapper and suddenly that gave me the same CRC Failed error.

Anyway, since I can still boot into Ubuntu, it must be a problem with the GRUB configuration, right?  Any advice on what I need to do?

---

