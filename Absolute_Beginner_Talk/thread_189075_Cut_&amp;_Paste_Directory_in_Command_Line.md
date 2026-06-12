---
title: "Cut &amp; Paste Directory in Command Line"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by TrendyDark on 2006-06-04
How would I move a directory from one place to another using the command line? :-?

---

### Post by harishg on 2006-06-04
zip the directory and move it.

---

### Post by aysiu on 2006-06-04
Use the *mv* command.

```
sudo mv /usr/share/backgrounds /usr/share/backgrounds_old
``` or ```
mv ~/.kde ~/.kde_backup
```

---

### Post by psquared89 on 2006-06-04
use the move command: "mv"

example:
```

mv /home/pat/test/ /home/pat/test1

```

This will move the folder "test" and its contents into "test1", the directory test will be deleted and test1 will be created.

---

### Post by TrendyDark on 2006-06-04
Thanks for the quick responses, much appriciated.

---

