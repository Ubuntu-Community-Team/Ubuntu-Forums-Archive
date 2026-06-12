---
title: "fat partition with ASCII filenames."
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by shadowfist on 2006-03-02
I was having a problem with permissions on my fat volume and i fixed it with the umask option but now I have discovered that i can access all the files but some of them show up with ??s in the name and these files I can still access the information but I cannot modify them. (they open up read only) is there a way to change the way the mounting reads the characters so its ASCII (instead of ISO or something)?

---

### Post by Pragmatist on 2006-03-03
can you give some examples of files with and without the **??**

---

### Post by shadowfist on 2006-03-03
now that i look at it it dosent seem to be related to the ?? folders.

just poking around on the fat partition revealed that there are several read only files. for example for some reason the "program files" folder is read only but the subfolders are full access. the is one random text file that is in the root of C:\ that is read only. and other just random folders like that. it just so happens that one of the random folders affected is one with some ascii characters in its name

---

### Post by Pragmatist on 2006-03-03
Read this, it might help. ```
man chmod
```

---

