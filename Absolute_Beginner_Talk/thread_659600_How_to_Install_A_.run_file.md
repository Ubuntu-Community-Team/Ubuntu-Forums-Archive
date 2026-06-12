---
title: "How to Install A .run file"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by x02flash on 2008-01-05
Hello. I was following the .run file howto in the tips section, but everytime i get to the point where I enter the "./file.run" command, i get the following error
```
root@alex-laptop:/home/alex/Desktop# chmod +X et-linux-2.55.x86.run
root@alex-laptop:/home/alex/Desktop# ./et-linux-2.55.x86.run
bash: ./et-linux-2.55.x86.run: Permission denied
root@alex-laptop:/home/alex/Desktop# 
```

I'm running Ubuntu 7.10

Any solutions?

---

### Post by yabbadabbadont on 2008-01-05
```
chmod +x et-linux-2.55.x86.run
```
Linux is case sensitive.  i.e. "X" != "x"  :)

---

### Post by x02flash on 2008-01-05
> **yabbadabbadont said:**
> ```
chmod +x et-linux-2.55.x86.run
```
Linux is case sensitive.  i.e. "X" != "x"  :)

yep, that was it.  thanks much

---

