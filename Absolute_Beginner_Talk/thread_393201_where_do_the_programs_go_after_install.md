---
title: "where do the programs go after install"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-25
example: sudo apt-get install swisswatch. 
i installed this program where do i find it after? it happends with many small program.

---

### Post by taurus on 2007-03-25
Most of them are resided in /usr/bin.  Open a terminal and see if you can run it from there.

Applications -> Accessories -> Terminal
```
swisswatch
```

---

### Post by eljalill on 2007-03-25
Also the "locate" command is pretty handy for this:
try typing 
```
locate swisswatch
```
into a terminal.
In the output should be all files and directories with that name

---

