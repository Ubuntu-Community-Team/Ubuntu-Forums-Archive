---
title: "How to change RPM to DEB"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by doctorj on 2007-05-26
Hi all,

I have seen this answer before but cannot find it by searching. How can I change a downloaded RPM file into a DEB so that I can install it?

I know the answer is simple but cannot find it.

Any help gratefully accepted.  :D

---

### Post by Nikron on 2007-05-26
Well, currently there's no fully stable way to do it.  You can use a program called 'alien'  But compiling from source would be best if there's no deb avaiable

---

### Post by taurus on 2007-05-26
```
sudo aptitude update
sudo aptitude install alien
alien **filename**.rpm
sudo dpkg -i **filename**.deb
```

---

### Post by doctorj on 2007-05-26
MAGIC!

It did the job perfectly well.

Thanks for all the help.  :D

---

### Post by Malibu Illusion on 2007-05-26
To be honest, I'd strongly suggest you take on board Nikron's comments.

Alien is a solution but, as they state themselves, largely experimental with many issues.  

In the event that no debs are available and you wish to install something, compiling from source would be advisable in the vast majority of cases.

Take care.

---

