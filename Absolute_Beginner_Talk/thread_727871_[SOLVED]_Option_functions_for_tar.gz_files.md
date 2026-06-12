---
title: "[SOLVED] Option functions for tar.gz files"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by rbc on 2008-03-18
Two questions that are not going to stop the world from spinning if I don't get an answer, but I have seen the command "tar -xzvf nameoffile.tar.gz" in tutorials, both with and without the hyphen. Which is correct, or does it not matter? Also, I read somewhere that the "x" option has to come first. After that, does it matter in which order the "z", the "v" and the "f" options go?

---

### Post by hyper_ch on 2008-03-18
well, regarding the hypher, consult the man pages and read up how they do it there... I think you don't need it....

I normally use xvfz --> that works also... I guess only the x is important (if at all).

---

### Post by handydan918 on 2008-03-18
IIRC, I have run tar against the xzvf combo with both x and z in first place....
Be that as it may, the f and v operators should be interchangeable too.

See man tar for more detail.

---

### Post by Oldsoldier2003 on 2008-03-18
> **handydan918 said:**
> IIRC, I have run tar against the xzvf combo with both x and z in first place....
Be that as it may, the f and v operators should be interchangeable too.

See man tar for more detail.

usually in gnu linux commands the option order doesn't matter when you batch the options, unless one of the options does something that could exclude another of the options- then it becomes very important. when in doubt use man <command>

---

### Post by rbc on 2008-03-18
Wonderful. Thanks all!

---

### Post by handydan918 on 2008-03-18
> **Oldsoldier2003 said:**
> usually in gnu linux commands the option order doesn't matter when you batch the options, unless one of the options does something that could exclude another of the options- then it becomes very important. when in doubt use man <command>

Right, I think that's a good rule of thumb, but again, IIRC, tar.bz files are order-sensitive, for example.

---

