---
title: "Installing a run file"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by cacharreo on 2006-10-22
How to intall a .run file? I have tried with *chmod -x* but nothing succes. Whe I try to run it it's edited by gedit

---

### Post by Najand on 2006-10-22
Hmm, use ```
chmod +x <filename>
```

and then run it.

---

### Post by po0f on 2006-10-22
cacharreo,

Readd execute permission to the .run file and just execute it:
```
$ cd /path/to/foo.run
$ chmod u+x foo.run
$ ./foo.run
    OR
$ sh ./foo.run
```

---

### Post by cacharreo on 2006-10-22
Thank you it works !!
:p

---

