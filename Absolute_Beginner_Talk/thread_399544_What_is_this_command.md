---
title: "What is this command?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-04-02
I was told by a friend that :

format c:\ is the same as rm -rf *

rm -rf* does what exactly?  I understand the rm, but what is -rf* ?  Thanks for the clarification.

---

### Post by trent dillman on 2007-04-02
..

---

### Post by finferflu on 2007-04-02
The flags -rf stand for:

-r (recursive): remove directories and their contents recursively

-f (force):  ignore nonexistent files, never prompt

you can find out more about commands by typing:

```
man <command>
```

where man stands for manual, 
hope it helps ;)

---

### Post by jhenager on 2007-04-02
Kinda sorta, but only in net effect.
Since 'format' is a DOS command, it would be more accurate to say 'del *.*' is the same as rm *.
formatting also writes a new FAT or directory table.

---

### Post by 3rr0r on 2007-04-02
so If I cd'd to / then did:
```

rm -rf *

```
It would delete everything.  Ouch

---

