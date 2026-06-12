---
title: "make clean and kernel compilation"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by ragas on 2007-12-04
Do I always need to do a make clean before I build the kernel again, after I make some  modification in the .config file? 

The problem is, if I do a make clean, building the whole kernel again takes a long time. Building the kernel without doing a 'make clean' completes very fast (as most of the files are already compiled). So, does not doing a 'make clean' affect my build in any way?

---

### Post by m0biu5 on 2007-12-04
```
make clean
```

Just cleans up files created during compilation. If you don't clean up, it will go faster because unchanged files need not be recompiled. You should not have any trouble recompiling without cleaning first, afaik.

---

