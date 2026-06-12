---
title: "find vs grep"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by sgargabonzi on 2007-04-29
hey fellas, 
Im a novice .. 
quick question:
what is the difference between grep and find. I mean, when do we decide to use one instead of the other? 

Enjoy spring.
Sgargabonzi

---

### Post by yabbadabbadont on 2007-04-29
find searches for files and directories that match a user specified set of criteria.  grep searches the contents of files for patterns that match those provided by the user.

Read the man pages for find and grep for details.  (man find, man grep)

---

### Post by sgargabonzi on 2007-04-29
makes sense. thank you!

---

### Post by K.Mandla on 2007-04-29
find scours your drive looking for a certain series of letters -- like a file name or something. Like this: 

```
find ~/documents/ -iname "*resume*"
```
That would look through a folder called "documents" for anything that included the word "resume" in the filename.

grep sifts through text output -- like from the context of a file -- for a certain string of characters. So 

```
cat /proc/cpuinfo | grep model
```
should spit out a single line that shows the model name of your processor -- because the cat command dumps the contents of the /proc/cpuinfo file, and grep spits out only the line that contains the word "model".

So use find to look for a file, use grep to sift through the contents of a file or output. Of course, they both have other uses too. 

Does that help? :)

---

### Post by sgargabonzi on 2007-04-29
it definitely helps. thanks a lot for the quick feedback guys.

---

