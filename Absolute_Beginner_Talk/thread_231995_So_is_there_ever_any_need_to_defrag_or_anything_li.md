---
title: "So is there ever any need to defrag or anything like that?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-08-08
Maybe I'm just overlooking them, but I've noticed that Ubuntu doesn't have any maintinence programs that usually come with Windows such as disk cleanup and disk defragger. Is there ever a need to do this, or is Ubuntu just so awesome it takes care of said actions on it's own or what?

---

### Post by MrHorus on 2006-08-08
> **Amablue said:**
> Is there ever a need to do this, or is Ubuntu just so awesome it takes care of said actions on it's own or what?

Not Ubuntu no, but it makes use of a journaling filesystem that is "intelligent enough" so defrag as it goes along so in theory, you never need to rnu a defrag like you do with NTFS or FAT/FAT32

---

### Post by arjun.shankar on 2006-08-08
No, not really. Fragmentation is not that big a problem on linux. Atleast thats what most users say. However if you must:

**$ sudo apt-get install defrag**

will get you a defragment program.

Then use the standard **$ man defrag** to learn how to go about using it.

EDIT: See? MrHorus says so too! defragging seems to be mainly a Windows job.

---

### Post by MrHorus on 2006-08-08
> **arjun.shankar said:**
> 
EDIT: See? MrHorus says so too! defragging seems to be mainly a Windows job.

And as they teach kids in school, if MrHorus says it then it *must* be true! :P

---

