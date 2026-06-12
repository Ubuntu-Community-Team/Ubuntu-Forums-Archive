---
title: "explain this command please"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by phoenix24x on 2007-11-01
```
grep $username /etc/passwd | cut -d: -f3
```

i understand that grep searches for *$username* in /etc/passwd, and then that output is entered as input (via the | ) to: ```
cut -d: -f3 
```

what does the:  ```
cut -d: -f3 
``` do?

---

### Post by ronald.higgins on 2007-11-01
-d is for delimiter, so where there is a : it recognises it as the end of a field, -f3 then selects the 3rd field.

---

### Post by dburnett77 on 2007-11-01
frum the cut word, cut, I'd say it is what is refered to as a truncate.

Seems to be an attempt to instill chosen passwords for various areas of the system, where there is not much security, then balloon from there.

---

### Post by nick_h on 2007-11-01
I think you actually want:
```
grep $USERNAME /etc/passwd | cut -d: -f3
```
which will return the userid for the current user.

As ronald.higgins said it will return the 3rd field from the file, which in /etc/passwd is the userid field.

---

