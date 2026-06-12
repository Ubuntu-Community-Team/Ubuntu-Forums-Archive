---
title: "MBR help"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by illegalamigo on 2006-09-10
Hi, after trying everything (even asking in these forums a couple times) I just could not get Linux to work for me. I had a dual boot with Ubuntu and Windows XP. Well, I reformatted the UBuntu partition from Windows and it messed up the boot loader. I can't install a new one and I can't use the windows resources because it hangs on the CD. I think this is because there is no boot record now. Please help me, I'm running on Knoppix 'til I can log into XP.

Thanks.

---

### Post by Stew2 on 2006-09-10
Hi. Check out [this]("http://www.users.bigpond.net.au/hermanzone/p18.htm") link, it has instructions on repairing your MBR. You need an actual XP install disc for this though, not a factory restore disc. Hope it helps.

Regards,
Stew2

---

### Post by Solver on 2006-09-10
You can't boot from the Windows setup CD? If so, that shouldn't be because of the broken MBR. If you can, run the Windows Setup CD, choose to enter recovery mode, and use the command fixmbr. That will fix your MBR so Windows will boot. You'll still want to do something with the Ubuntu partitions, though.

---

