---
title: "command line for newuser to have sudo permission"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-05-09
what is the command line for a new user to have sudo permissions?

lex1

---

### Post by trent dillman on 2006-05-09
...

---

### Post by cgjones on 2006-05-09
I think all you need is the following:
```

sudo usermod -G admin *username*

```

---

