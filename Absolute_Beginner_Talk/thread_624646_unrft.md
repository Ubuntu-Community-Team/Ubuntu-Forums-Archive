---
title: "unrft"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by lex1 on 2007-11-27
i am useing a small package called unrft

at command line i run as below
 

to convert the rtf file to a text file 

but then i get this useage screen what am i doing wrong?


~/Desktop$ unrtf --text admink.rtf adminq.text
Usage: unrtf [--version] [--help] [--nopict|-n] [--html] [--text] [--vt] [--latex] [--ps] [--wpml] [-t html|text|vt|latex|ps|wpml] <filename>


thanks

lex1:popcorn:

---

### Post by ephro on 2007-11-27
I would assume you have to pipe to output, try the following:

```
unrtf --text admink.rtf > adminq.text
```

ephro

---

