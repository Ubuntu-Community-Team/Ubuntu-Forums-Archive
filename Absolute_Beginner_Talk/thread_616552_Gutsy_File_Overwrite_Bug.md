---
title: "Gutsy File Overwrite Bug"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-11-18
When i try to copy a file/folder into a folder where it already exists using the GUI, it asks me if i want to skip or replace, skip does the expected behavior, but clicking replace let the directory structure exist in case of folder, but delete all similar files. I haven't tried it using shell....

I have aliased mv, cp, rm by their -iv versions, but that can't do such stupid things, and even those are bash profile settings, not the nautilus settings...


So is it a bug?

---

### Post by finer recliner on 2007-11-18
> **shoaibi said:**
> ...but clicking replace let the directory structure exist in case of folder, but delete all similar files. 



i don't understand. please try to explain it again in a different way, or give an example.

---

### Post by shoaibi on 2007-11-19
Directory structure before:

-Folder 
-> Folder 1
->>File 1
->>File 2
->>File 3

->Folder 2
->>File 1

->File 1


This data below is to be copied over the structure given earlier:


-Folder 
-> Folder 1
->>File 1
->>File 2
->>File 3
->>File 4

->Folder 2
->>File 1


What i get by clicking replace will be:


-Folder 
-> Folder 1
->>File 4

->Folder 2

->File 1

e.g. the directory struture is preserved but the files that were to be over-written got delete instead...

[EDIT]:
This is kind of my own file tree.
- represents the main directory in which i am copying.
> represents every level under that directory.
Don't get confused by same filenames...
This was the best example that i could give, have you got it, or should i clear it by some other example? :(

---

