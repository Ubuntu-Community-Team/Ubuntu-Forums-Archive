---
title: "rename many files"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by widjajayd on 2006-02-24
have many files in my repository and some of them with % in the middle of file name

I want to erase % from file name do you know what command should I use

rename .... ???

please suggest

thank you guys

---

### Post by Stormy Eyes on 2006-02-24
Back up the files you want to rename (in case this suggestion doesn't work) and try the following.

```
for e in *; do mv "$e" "`echo $e | sed -e 's/\ /_/g'`"; done
```

I advise you backup before trying this because I am away from my Linux box and don't use sed very often. If this doesn't work, I'll post later when I'm home from work.

---

### Post by transactionlogfiller on 2006-02-24
The given command seems to be replacing spaces with underscores. If it's the % character you want to get rid of you could do it in a similar way.

```

for e in *; do mv "$e" "`echo $e | sed -e 's/%//g'`"; done

```

---

### Post by Stormy Eyes on 2006-02-24
[QUOTE=transactionlogfiller]The given command seems to be replacing spaces with underscores. If it's the % character you want to get rid of you could do it in a similar way.

```

for e in *; do mv "$e" "`echo $e | sed -e 's/%//g'`"; done

```[/QUOTE]

Oops. That's what I get for copying, pasting, and quickly alt-tabbing back to work to babysit some admin stuff. Sorry about that.

---

