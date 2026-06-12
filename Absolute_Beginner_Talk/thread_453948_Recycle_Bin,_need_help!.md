---
title: "Recycle Bin, need help!"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by adt41287 on 2007-05-24
ok here is my problem (sorry for hogging the forums) i have 3 different partitions that i use in ubuntu but the recycle bin seems to only keep track of the primary partition that you are running off from... how do you make it so the other folders or "recycle bins" for the other drives work with the main recycle bin icon??

---

### Post by Ek0nomik on 2007-05-24
Well, you could create shortcuts to each partitions .trash folder.  I don't think you can get a single trash folder to look at the .trash on all partitions.

You would either have to have all the data get moved to the single partition where you want the trash to reside, or have shortcuts to each file created upon deletion.

I can't think of an easy way to do it, and I couldn't find anything showing how to do it.

---

### Post by adt41287 on 2007-05-24
> **Ek0nomik said:**
> Well, you could create shortcuts to each partitions .trash folder.  I don't think you can get a single trash folder to look at the .trash on all partitions.

**You would either have to have all the data get moved to the single partition** where you want the trash to reside, or have shortcuts to each file created upon deletion.

I can't think of an easy way to do it, and I couldn't find anything showing how to do it.

thats what i was looking for, do you know of an easy way to do this??

---

### Post by Ek0nomik on 2007-05-24
Well, personally I wouldn't suggest it because it's kind of a waste of time.  The data has to get transfered from partition to partition, and it's just eating up processor speed.

But, if you really want to do it, you could maybe write a script that handles it, but I don't know for sure, or if one even exists already for it.  Otherwise you could maybe write a script that automatically deletes the .trash folders every 2 days or something like that.

I don't know if this is possible, but I see people writing scripts quite frequently, and I imagine it being possible, the latter of the two especially.

Sorry, I can't really help specifically, just trying to throw you some ideas so maybe you can get it working.  :)

---

