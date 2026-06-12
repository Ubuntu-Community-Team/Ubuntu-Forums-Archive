---
title: "Bytes, megabytes and gigabytes"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ImpelGD on 2007-04-19
I'm just creating my partitions in the Ubuntu installer:
> New partition size in megabytes (1000000 bytes):
If I want a 1GB partition, what is the correct value? 1000? 1024?

Thanks.

---

### Post by Iceni on 2007-04-19
Here is a horribly long and boring text about gigabytes, megabytes and bytes:

[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

I'd say 1000 mb:)

---

### Post by ImpelGD on 2007-04-24
It seems neither 1000 or 1024 MB gives a "GB". If I make the swap partition 4096 MB it's stated as being 3.815 GB post installation.

Can anyone shed some light? Thanks.

---

### Post by Bachstelze on 2007-04-24
That's because some programs calculate sizes with powers of 1000 and others with powers of 1024 but, honestly, what does it matter if your partition is 4 GB or 3,815 GB ?

---

### Post by Cicatrix on 2007-04-24
perhaps the correct value  is **1024*1024** instead of 1000*1024 or 1000*1000?

---

### Post by ImpelGD on 2007-04-24
> **HymnToLife said:**
> That's because some programs calculate sizes with powers of 1000 and others with powers of 1024 but, honestly, what does it matter if your partition is 4 GB or 3,815 GB ?

But I went with 1024 (intending to end up with 4GB), and Windows still reports 3815 GB. And it matters because I'm a perfectionist. :)

> **Cicatrix said:**
> perhaps the correct value  is **1024*1024** instead of 1000*1024 or 1000*1000?

Sorry; I don't follow.

---

### Post by freebird54 on 2007-04-24
NO matter what you choose - just to make it harder - the partitioning progarms willl round it to the nearest convenient block matching size.  Which varies with the OS, and its settings.  So - goodluck with that!  :)

---

### Post by ImpelGD on 2007-04-24
Sure, but block sizes wouldn't be responsible for nearly two-tenths of a gig, right?

I'm missing something here and would really like to know what, even if only for educational purposes.

---

### Post by freebird54 on 2007-04-24
What you are missing is the Mb are also (incorrectly) defined as 1000, rather than 1024.  So, do your math, correct for that, then hope the result isn't changed much by the  block boundary (actually, usually track boundary) considerations.  So, I guess you multiply your 4096 by 1.024, and then try that...

Enjoy!

---

### Post by ImpelGD on 2007-04-24
> **freebird54 said:**
> What you are missing is the Mb are also (incorrectly) defined as 1000, rather than 1024.  So, do your math, correct for that, then hope the result isn't changed much by the  block boundary (actually, usually track boundary) considerations.  So, I guess you multiply your 4096 by 1.024, and then try that...

Ah, thanks for spelling it out for me! :)

Will try soon.

---

### Post by freebird54 on 2007-04-24
At that - you have to hope that the Kb were also 1024 - so you may need another 'adjustment'.  It really is rather silly how it varies from place to place.  The only thing you can count on is that hard drive makers will describe the drive capacity in the biggest way they can!

---

### Post by mshale on 2007-04-25
if one used GParted, instead of the editor in the feisty install... one could calculate it exactly using 1024 as 1 gigabyte.  gparted uses a live cd just as the feisty install disk, that way you can get all of your partitions like you like them before the install!!  

Happy Partitioning!

---

