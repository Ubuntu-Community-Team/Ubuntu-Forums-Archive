---
title: "copying files in order to move /home"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-05-08
I was considering moving my /home directory to a separate partition. Psychcats have some instructions that use this command

```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

but I was wondering why you wouldn't just use cp, maybe with a   -a   option?

---

### Post by gradedcheese on 2007-05-08
From the looks of the cpio man page, they might be doing this to ensure that file ownerships are perfectly preserved, which is definitely something you want.

---

### Post by ubnewbie2 on 2007-05-09
> **gradedcheese said:**
> From the looks of the cpio man page, they might be doing this to ensure that file ownerships are perfectly preserved, which is definitely something you want.

but as I understand it, that's exactly what     cp -a    does

---

### Post by dwblas on 2007-05-09
cp -av /original_dir/* /new_home_dir/ will work fine.  Note the single asterisk.  tar is another to do it as well, which is what I usually use, but either is fine.

---

### Post by gradedcheese on 2007-05-09
Ah yeah, you know, I think you're right.  If you have some spare time, maybe do a test with cp -a and then ls -al the contents and see if there are any permission and owner/group differences between the two methods.  However I think cp -a would indeed work.

---

### Post by ubnewbie2 on 2007-05-09
Yes, I'll be trying that tonight (or soon anyway).  Thanks.

---

