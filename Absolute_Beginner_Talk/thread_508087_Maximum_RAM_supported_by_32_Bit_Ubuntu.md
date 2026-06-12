---
title: "Maximum RAM supported by 32 Bit Ubuntu?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-07-23
The board I'm getting for my new system supports up to 24GB, but I read in a few places that the OS sometimes can't utilize that much. I've seen lots of websites with people saying that Winblows XP can only utilize and reports only 3GB of ram, and I plan on purchasing 4GB for my system.

What is Ubuntu's max?

---

### Post by Zzl1xndd on 2007-07-23
> **kavon89 said:**
> The board I'm getting for my new system supports up to 24GB, but I read in a few places that the OS sometimes can't utilize that much. I've seen lots of websites with people saying that Winblows XP can only utilize and reports only 3GB of ram, and I plan on purchasing 4GB for my system.

What is Ubuntu's max?

32bit systems can support up to 4 gigs but that is including your swap.

---

### Post by atlfalcons866 on 2007-07-23
32 bit cpus can acess up to 4GBs of ram.so that means ubuntu only has 4Gigabytes. IF you want support for more than 4Gbs you need a 64bit cpu

---

### Post by kavon89 on 2007-07-23
> **tweakedenigma said:**
> 32bit systems can support up to 4 gigs but that is including your swap.

Including my Swap? I prefer to run the Ubuntu installer on "easy mode" so I let it configure my whole drive the way it likes. Will it notice I have 4GB of fast RAM and decide to skip the swap? Or make like a little 128MB swap because it needs some sort of swappage?

Does it make any difference if I will be running 2 separate CPUs? Does that mean 4GB per chip?

---

### Post by atlfalcons866 on 2007-07-23
what type of cpu do you have

---

### Post by Zzl1xndd on 2007-07-23
Swap is only used when you go over the amount of ram you have, I would just skip it I don't think this is gonna be an Issue.
You could install the 64bit edition but that could give you a number of other issues but it would support a  lot more ram.

---

### Post by briealeida on 2007-07-30
Not including swap a 32 bit OS can only support how much RAM?

And I heard of a switch in the kernel (forget what it's called) that would allow the machine to recognize over 3 GB after I recompiled it. Is this the case?


edit: And what about PAE?

---

### Post by Depressed Man on 2007-07-30
swap isn't included as part of physical RAM. So a 32 bit OS can only have 4 GBs of physical RAM.

---

