---
title: "[SOLVED] Help with Totem in the terminal"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by whitethorn on 2008-01-07
Hi I'm trying to figure out a way to get totem to open more than one file in one command line.  It should start playing the file and enqueue the others. 

I get it work for 1 file.  So totem /..../asdf.mp3   but instead of just one for like 2-3 songs.

---

### Post by RomeReactor on 2008-01-07
Hi. If you have all the files you want to open in Totem in a single folder, you can do it like this:
```
cd /PATH/TO/FOLDER
```
then:
```
totem --enqueue *
```

---

