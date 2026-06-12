---
title: "date format on terminal with ls -l"
date: 2014-06-16
forum: Any Other OS
---

### Post by Alberto_M._Lopez on 2014-06-16
Anybody knows how to change the date format when invoking "ls -l " on the command terminal?  
Currently I get Month Day Year and I want YEAR-MM-DD format including those dashes.  And
it is not with the locale.  I use en.US-UTF8 on an older linux system and it does prints  it the way I want it to be, so I don't need to change it to ISO.
I have seen other forum comments about it but not much and they do not solve the problem.
Any thoughts? They will be highly appreciated.  Thanks.

---

### Post by rahul4557 on 2014-06-17
try this command

> ls -l --full-time

---

### Post by philinux on 2014-06-17
Also check the man page for ls.

```
man ls
```

---

### Post by Alberto_M._Lopez on 2014-06-17
Any idea how to make this on a BSD system?

---

### Post by philinux on 2014-06-17
Moved to other os support.

---

### Post by Lars Noodén on 2014-06-17
Which BSD in particular?  PC-BSD, FreeBSD, OpenBSD, OS X, etc.

---

