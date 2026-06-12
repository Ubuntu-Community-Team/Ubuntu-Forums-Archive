---
title: "How do I 'ls' files with size display in current folder?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-05-20
How do I 'ls' files with size display in current folder?

I can not figure out how to use this --block-size=size option.  At least I think this is the option to use if I want to find out the sizes of all the files in the current directory.

---

### Post by macdo on 2006-05-20
Try ```
ls -l
```

The size is just before the date.

---

### Post by halfvolle melk on 2006-05-20
Adding 'h' will make it 'human readable'
```
ls -lh
```

---

### Post by macdo on 2006-05-20
Cool! I've been battling with bytes for so long now I can nearly convert in my head! If only I had known...

---

### Post by ProjectGod on 2006-05-20
try:

**ls --help** for more options...

i like using:

**ls -sh**

this displays size in "human" format ;)

---

