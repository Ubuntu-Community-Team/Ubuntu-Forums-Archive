---
title: "Delete Windows partition, save rest"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by tommytwo on 2007-01-27
I have a 13gb hard drive and 7.45gbs is used by the windows partition.  
It has been over 3 months since windows has been booted.
Is there any way to remove the windows partition without destroying Ubuntu?
:confused: Absolute beginner

---

### Post by taurus on 2007-01-27
Yes.  Just install gparted and use it to reformat your Windows partition.  Convert it to ext3 so you can use it as a storage for Ubuntu.

```
sudo aptitude update
sudo aptitude install gparted
```
It will be under System -> Administration.

---

