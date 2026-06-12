---
title: "Path Question"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by lex1 on 2007-09-16
From root i use  root to invoke a command the result is that for example
the command " tail" is not found

tail resides in user/bin/tail

the PATH from root is
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


how should i change my PATH and how


thanks  lex1

---

### Post by por100pre1 on 2007-09-16
> **lex1 said:**
> From root i use  root to invoke a command the result is that for example
the command " tail" is not found

tail resides in user/bin/tail

the PATH from root is
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


how should i change my PATH and how


thanks  lex1

Did you check where "tail" is?

```
which tail
```

```
locate tail
```

In my case which tail gives me /usr/bin/tail

---

### Post by lex1 on 2007-09-16
tail is in /usr/bin
but when i invoke the command from root tail command not found
lex1

---

### Post by nonewmsgs on 2007-09-16
make sure the capitalization is correct.

(by the way that's funny about having trouble finding tail)

---

### Post by jw5801 on 2007-09-16
How exactly are you trying to run the command as root? ```
sudo tail *file*
```?

Heh. My tail resides in my bin...

---

