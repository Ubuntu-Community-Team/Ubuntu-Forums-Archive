---
title: "empty file"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by timon_tg on 2007-01-26
hi,
can anyone tell me a command or any way to clear content of a file? without deleting and recreating the file again!
10x

---

### Post by lamego on 2007-01-26
Please read about it here:
[http://ubuntuforums.org/archive/index.php/t-243881.html](http://ubuntuforums.org/archive/index.php/t-243881.html)

---

### Post by Arndt on 2007-01-26
> **timon_tg said:**
> hi,
can anyone tell me a command or any way to clear content of a file? without deleting and recreating the file again!
10x

If all you want is just to make the file become empty, not erase the previous contents irretrievably from the disk (by overwriting and so on), just do

```
$ : > myfile

```

Looks like some kind of smiley, but '$' is the prompt, ':' is the command (the do-nothing command in sh). Note that this creates the file if it didn't exist already.

---

### Post by timon_tg on 2007-01-29
Arndt 10x , this was the command I needed !

---

