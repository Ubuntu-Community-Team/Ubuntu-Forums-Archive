---
title: "Ubuntu 7.10 won't install or boot on old laptop"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by DeadnightWarrior on 2008-02-02
Hello, I'm relatively new to the Linux world, so I hope you'll be able to solve my little problem. 
I have an old Clevo 2800T laptop (Celeron 1.3, 256 Mb ram, SiS chipset) and want to install a Linux distribution on it. 
I tried Ubuntu 7.10 x86, but I can't seem to get past the boot menu. 
If I select "Install Ubuntu", I get this message: 

*[BIOS age (1997) fails cutoff (2000) acpi=force is required to enable ACPI]*

And if I try to boot the "live" OS, the process hangs with a "kernel panic" error: 

*[Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)]*

I DID update the machine's BIOS (and believe me, it's not that easy to find a newer BIOS for this model!), but strangely enough, the BIOS itself doesn't seem to care and it still shows the year 1997 (while the new one should be 5 years younger - 2002 ).

Any suggestions? 

Thanks!

---

### Post by Bodsda on 2008-02-02
Hey, the bios cutoff at 2000 is like the millenium bug, old bios's believe the entire world ends in 2000. So to begin with the bios should be updated to realise that the world still exists, then i would suggest trying the text installer aka alternate installer,

---

### Post by ijason on 2008-02-02
it may be that you have a laptop which is incompatible with the 7.10 version of ubuntu. i'm not sure where the direct link is, but if you should be able to find it via a google search. the list of acceptable hardware, i mean.

i have a fairly old machine running 7.10, a desktop i believe that is at least as old... so i don't think it's specifically the age of your machine. you may need an older version of ubuntu.

---

### Post by DeadnightWarrior on 2008-02-02
> **Bodsda said:**
> Hey, the bios cutoff at 2000 is like the millenium bug, old bios's believe the entire world ends in 2000. So to begin with the bios should be updated to realise that the world still exists, then i would suggest trying the text installer aka alternate installer,

I already tried to update my BIOS, but for some reason, it still appears as 1997. I don't know why, the updating process ran just fine with no problems. 

How can I install in text mode? Is there a specific console command I have to type?

---

### Post by ijason on 2008-02-02
the custom install requires, i believe, a different cd than the normal install. check out the download page for more details. good luck!

---

### Post by DeadnightWarrior on 2008-02-03
> **ijason said:**
> the custom install requires, i believe, a different cd than the normal install. check out the download page for more details. good luck!

All right, I'll give the alternate a try... 
Thank you for now!

---

