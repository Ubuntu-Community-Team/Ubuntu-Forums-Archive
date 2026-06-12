---
title: "Empty trash from terminal"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-10-03
Would "rm -f ~/.Trash" empty my trash can

---

### Post by tszanon on 2007-10-03
> **bloor75 said:**
> Would "rm -f ~/.Trash" empty my trash can
```
rm -Rf ~/.Trash/*
```
Added **-R** for recursiveness, and **/*** at the end just for me to make sure that .Trash itself won't be deleted. :)

---

### Post by ignorance on 2007-10-03
I never did it with /* one way or another my .Trash map always came back.

---

### Post by swoll1980 on 2007-10-03
Thanks. What is recursiveness?

---

### Post by Callius on 2007-10-03
> **bloor75 said:**
> Thanks. What is recursiveness?

Recursive means that it will affect all of the folders/files that are "below" it in it's file tree.

So, say you have ~/.trash/Anime/Akira

If you do "rm -f ~/.trash" it will delete the files in ~/.trash; but will leave the folder link Anime/Akira.

However, if you do "rm -fr ~/.trash/" it will delete all folders below ~/.trash *recursively*.  So, it will delete everything in ~/.trash, everything in ~/.trash/Anime and everything in ~/.trash/Anime/Akira.

Make sense?



Mind, I'm a total linux newbie too, but this is how I understand it to work.

---

