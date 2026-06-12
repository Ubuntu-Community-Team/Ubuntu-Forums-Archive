---
title: "linux command"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Oldsoldier2003 on 2008-03-31
> **Auston said:**
> Hi there

Does anybody know any command that can search in all text files for a particular string. Imagine that you use a large Java package and you want to search for a particular class in the whole package. The command should be able to look into sub-folders as well. I will be really thankful  if anyone could post an example.

Thanks

grep

see```
 man grep
```

```
cd somedir
grep -i "somestring" *
```

---

### Post by Inxsible on 2008-03-31
find is also another command that might be useful to you. ```
man find
```

---

### Post by t0p on 2008-04-01
If you wanna learn some commands, check out the link in my sig.

---

