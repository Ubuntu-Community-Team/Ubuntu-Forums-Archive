---
title: "join many mpg"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-10-07
hi,
i've got some mpegs movie and i'd like to merge them i one file.
Are there some sws for linux that do this job?
thanks

---

### Post by matthew on 2006-10-07
Make sure all the files are in the same location (i.e. /home/yourname)

Open a terminal (Applications->Accessories->Terminal)

Type```
cat clip1.mpeg clip2.mpeg clip3.mpeg > longmovie.mpeg
```where clip1.mpeg... are the clips you wish to join with a space between each name and longmovie.mpeg is the name you want them to have once joined.



EDIT: if they all have names in numerical/alphabetic order like clip1, clip2, etc. you can just use "cat clip*.mpeg > longmovie.mpeg"

also, this will work with mpeg's and mpg's but I don't think it works with wmv's

---

### Post by aysiu on 2006-10-07
If you install *mpgtx*, I believe you can do something like ```
mpgjoin *.mpeg
``` There are also some other options you can explore with *man mpgtx*.

---

### Post by ubunlilluz on 2006-10-07
with cat it seems that it works, thanks.

with avi i don't think that it will work, do you know some sw?

---

### Post by jhaquo on 2006-12-10
we cant delete our own posts? ](*,)

---

### Post by george1984 on 2007-05-21
Just what I needed. Simple and elegant. 

Thanks from this computer novice.

---

