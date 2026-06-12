---
title: "write to external"
date: 2007-12-25
forum: Apple Intel Users
---

### Post by brandon333 on 2007-12-25
cannot write to my external hard drive, so I am wandering if i can repartiton it into 2, 1 being mac journaled for my mac, other for ubuntu?

---

### Post by PmDematagoda on 2007-12-25
What do you mean you cannot write? If the hard drive has failed then you may not be able to partition it at all.

---

### Post by brandon333 on 2007-12-25
I have a maxtor 500 gig external drive hooked to my mac and I can read and write to it while in osx but can only read from it when on ubuntu, says I dont have permissions

---

### Post by PmDematagoda on 2007-12-25
What Filesystem does it have?

---

### Post by brandon333 on 2007-12-25
mac journaled which is no good right? So is there a format that both os's could read and write to, or can / should I partition the external, I have a mac mini which comes with very little space so I save all my files to the external to save space, I'd prefer that I could read and write same files on both osx and ubuntu but I would be happy with just being able to keep them separate too..1 partition for ubuntu and one for osx

---

### Post by PmDematagoda on 2007-12-25
You could try Fat32 or Fat16 as a sort of "intermediary" filesystem.

In any case, the partitioner I would recommend for almost anything is Gparted. You can install Gparted using:-
```

sudo apt-get install gparted
```

---

### Post by brandon333 on 2007-12-25
In disc utility it takes like 2 seconds and has a ms dos- fat option, maybe i will try that, if not off to gparted

---

### Post by PmDematagoda on 2007-12-25
Good luck with that:).

---

### Post by brandon333 on 2007-12-25
thanks it worked!

---

