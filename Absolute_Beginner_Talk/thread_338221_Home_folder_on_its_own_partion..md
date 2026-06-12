---
title: "Home folder on its own partion."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Oki on 2007-01-14
Wondering if;

Lets say I install Ubuntu Edgy on one partion and “home folder” get its own partion on the same disk. What happens when I later do a clean install with Feisty (meaning; no upgrade, but a install of the burned ISO file). Will the "old" home be deleted? Perhaps someone can tell med the benefit with letting home getting its own partion (i am the only one using the pc).

Thanks again!

---

### Post by Sef on 2007-01-14
> Lets say I install Ubuntu Edgy on one partion and “home folder” get its own partion on the same disk. What happens when I later do a clean install with Feisty (meaning; no upgrade, but a install of the burned ISO file). Will the "old" home be deleted?

No.  The home folder will be retained intact.   Only the root and swap will be formated.  That said, **back up** your data before doing a clean install.   There are no 100% guarantees.

---

### Post by rai4shu2 on 2007-01-14
Having /home on its own partition means you don't need to keep reformatting /home any time you do a clean install.

---

### Post by tribaal on 2007-01-14
No, during install (well if you use the advanced partitionning), you can tell your install porgram not to erase this particular partition, and then to use it as /home as well.

This works pretty well as far as I can tell, with the only problems being on an application bais (some config files are stored in your home, so if the software is a new version, the settings might be outdated).

Hope I make sense, I need some sleep :)

- trib'

---

### Post by Oki on 2007-01-14
Thank you all for your - again - good help :-D Just the answer I was hoping for! 

And god night trib he he (day here)

---

### Post by Sef on 2007-01-14
You're welcome.  Please post any other questions that you have.

---

