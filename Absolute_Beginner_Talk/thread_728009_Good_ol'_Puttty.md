---
title: "Good ol' Puttty"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by zebog13 on 2008-03-18
Putty is great because it shows the path I have taken while I SSH into my Ubuntu Server. Is there a way to show the file name when I am editing a file.

---

### Post by handydan918 on 2008-03-18
> **zebog13 said:**
> Putty is great because it shows the path I have taken while I SSH into my Ubuntu Server. Is there a way to show the file name when I am editing a file.

What are you using to edit the file? Doesn't it tell you what file you are editing?
at any rate, you can find out "where you are" with ```
pwd
```
(print working directory)

And you can see all the files in that working directory with ```
ls -a
```

---

### Post by zebog13 on 2008-03-19
> **handydan918 said:**
> What are you using to edit the file? Doesn't it tell you what file you are editing?
at any rate, you can find out "where you are" with ```
pwd
```
(print working directory)

And you can see all the files in that working directory with ```
ls -a
```

I think you misunderstood what I was trying to say.
If I ssh into ubuntu using Putty, the title bar states the path you are on. However, when I edit a file using vim, it does not append the filename. Is it possible to have the title bar to either append it to the path or just state the filename?

---

