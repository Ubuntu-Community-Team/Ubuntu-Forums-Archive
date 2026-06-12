---
title: "how to use the find command for hidden files?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-08-25
Is there a way to use the find command to search for hidden files?  For instance if I wanted to search the entire computer every directory for say the word dog including hidden folders/files how would I do this?

I tried doing a -a at the end, but keeps giving me an error.

I was doing a find . "dog" and that seems not to check hidden folders.

thanks in advance.

---

### Post by capink on 2007-08-25
```
find / -iname '*dog*'
```


Edit: To be able to search files on directories with limited permissions, use sudo:

```
sudo find / -iname '*dog*'
```

---

### Post by bone2006 on 2007-08-27
Thanks so much

---

